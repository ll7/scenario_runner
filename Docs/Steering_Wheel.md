# Steering Wheel

This tutorial describes how you can connect a Steering Wheel with the Carla Scenario Runner.

It explains the LTWheelConf tool, shows the most important changes and describes how to adjust the sensitivity of the steering wheel.

## I.) Get the LTWheelConf Tool for support

The following sources were used for the paragraphs I.) and II.): https://steamcommunity.com/sharedfiles/filedetails/?l=german&id=142372419

With the tool LTWheelConf it is possible on Ubuntu to make the following Logitech steering wheels fully functional (separate axles, full wheel ranges, clutch pedal, H-shifter):

    Driving Force
    Momo Racing
    Momo Force
    Driving Force Pro
    Driving Force GT
    G25
    G27

First you have to get some dependencies:
```
sudo apt-get install libusb-1.0-0-dev git jstest-gtk joystick
```
Second you can download the source:
```
git clone https://github.com/thk/LTWheelConf.git
```
Third then build the source with the following two commands:
```
cd LTWheelConf
```
```
make
```
Now you should have an executable file named ltwheelconf.

Finally install it with the following command:
```
sudo cp ltwheelconf /usr/local/bin/
```

## II.) Use LTWHeelConf to identify your steering wheel

In this paragraph we want to know whether our steering wheel is recognised and what the name or the shortname of our steering wheel is to use it later in the dual controller class.

To list all found/supported devices execute:
```
sudo ltwheelconf --list
```
These are a selection of supported wheel shortname values you can get with the LTWheelConf Tool:

    'DF' (Driving Force)
    'MR' (Momo Racing)
    'MF' (Momo Force)
    'DFP' (Driving Force Pro)
    'DFGT' (Driving Force GT)
    'G25' (G25)
    'G27' (G27)

## III.) Copy the DualControl Class in your manual_control.py 

Fortunately Carla already provides a class DualControl() under the following path, which we can reuse slightly modified for our manual control script of Scenario Runner.

So first copy the Dual_Control() Class from in the manual_control.py of your scenario runner:
```
/home/carlaws19/CARLA_0.9.9/PythonAPI/manual_control_steeringwheel.py
```

Then you have to some individual debug work depending on the Version of your manual_control_steeringwheel.py script from CARLA and your Version of your Scenario Runner manual_control.py.

For this purpose we have prepared an executable script as an orientation:

```
/home/carlaws19/scenario_runner/manual_control_steering_wheel.py
```

The most important change is to add the path and the name to your steering wheel script in the initialize() method.

For our case we had the "Logitech Logitech Formula Force RX".

To be honest, this name is different from the selected ones above but it works for our application.

The following is the modified DualControl class:

```
class DualControl(object):
    def __init__(self, world, start_in_autopilot):
        self._autopilot_enabled = start_in_autopilot
        self._autopilot_enabled = start_in_autopilot
        self._control = carla.VehicleControl()
        self._steer_cache = 0.0
        world.vehicle.set_autopilot(self._autopilot_enabled)
        world.hud.notification("Press 'H' or '?' for help.", seconds=4.0)

        # initialize steering wheel
        pygame.joystick.init()

        joystick_count = pygame.joystick.get_count()
        if joystick_count > 1:
            raise ValueError("Please Connect Just One Joystick")

        self._joystick = pygame.joystick.Joystick(0)
        self._joystick.init()

        self._parser = ConfigParser()
        #self._parser.read('wheel_config.ini')
        self._parser.read('/home/carlaws19/CARLA_0.9.9/PythonAPI/examples/wheel_config.ini')
        self._steer_idx = int(
            self._parser.get('Logitech Logitech Formula Force RX', 'steering_wheel'))
        self._throttle_idx = int(
            self._parser.get('Logitech Logitech Formula Force RX', 'throttle'))
        self._brake_idx = int(self._parser.get('Logitech Logitech Formula Force RX', 'brake'))
        self._reverse_idx = int(self._parser.get('Logitech Logitech Formula Force RX', 'reverse'))
        self._handbrake_idx = int(
            self._parser.get('Logitech Logitech Formula Force RX', 'handbrake'))
		# G29 Racing Wheel

    def parse_events(self, world, clock):
        for event in pygame.event.get():
            if event.type == pygame.QUIT:
                return True
            elif event.type == pygame.JOYBUTTONDOWN:
                if event.button == 0:
                    world.restart()
                elif event.button == 1:
                    world.hud.toggle_info()
                elif event.button == 2:
                    world.camera_manager.toggle_camera()
                elif event.button == 3:
                    world.next_weather()
                elif event.button == self._reverse_idx:
                    self._control.gear = 1 if self._control.reverse else -1
                elif event.button == 23:
                    world.camera_manager.next_sensor()

            elif event.type == pygame.KEYUP:
                if self._is_quit_shortcut(event.key):
                    return True
                elif event.key == K_BACKSPACE:
                    world.restart()
                elif event.key == K_F1:
                    world.hud.toggle_info()
                elif event.key == K_h or (event.key == K_SLASH and pygame.key.get_mods() & KMOD_SHIFT):
                    world.hud.help.toggle()
                elif event.key == K_TAB:
                    world.camera_manager.toggle_camera()
                elif event.key == K_c and pygame.key.get_mods() & KMOD_SHIFT:
                    world.next_weather(reverse=True)
                elif event.key == K_c:
                    world.next_weather()
                elif event.key == K_BACKQUOTE:
                    world.camera_manager.next_sensor()
                elif event.key > K_0 and event.key <= K_9:
                    world.camera_manager.set_sensor(event.key - 1 - K_0)
                elif event.key == K_r:
                    world.camera_manager.toggle_recording()
                if isinstance(self._control, carla.VehicleControl):
                    if event.key == K_q:
                        self._control.gear = 1 if self._control.reverse else -1
                    elif event.key == K_m:
                        self._control.manual_gear_shift = not self._control.manual_gear_shift
                        self._control.gear = world.vehicle.get_control().gear
                        world.hud.notification('%s Transmission' %
                                               ('Manual' if self._control.manual_gear_shift else 'Automatic'))
                    elif self._control.manual_gear_shift and event.key == K_COMMA:
                        self._control.gear = max(-1, self._control.gear - 1)
                    elif self._control.manual_gear_shift and event.key == K_PERIOD:
                        self._control.gear = self._control.gear + 1
                    elif event.key == K_p:
                        self._autopilot_enabled = not self._autopilot_enabled
                        world.vehicle.set_autopilot(self._autopilot_enabled)
                        world.hud.notification('Autopilot %s' % ('On' if self._autopilot_enabled else 'Off'))

        if not self._autopilot_enabled:
            if isinstance(self._control, carla.VehicleControl):
                self._parse_vehicle_keys(pygame.key.get_pressed(), clock.get_time())
                self._parse_vehicle_wheel()
                self._control.reverse = self._control.gear < 0
            elif isinstance(self._control, carla.WalkerControl):
                self._parse_walker_keys(pygame.key.get_pressed(), clock.get_time())
            world.vehicle.apply_control(self._control)

    def _parse_vehicle_keys(self, keys, milliseconds):
        self._control.throttle = 1.0 if keys[K_UP] or keys[K_w] else 0.0
        steer_increment = 5e-4 * milliseconds
        if keys[K_LEFT] or keys[K_a]:
            self._steer_cache -= steer_increment
        elif keys[K_RIGHT] or keys[K_d]:
            self._steer_cache += steer_increment
        else:
            self._steer_cache = 0.0
        self._steer_cache = min(0.7, max(-0.7, self._steer_cache))
        self._control.steer = round(self._steer_cache, 1)
        self._control.brake = 1.0 if keys[K_DOWN] or keys[K_s] else 0.0
        self._control.hand_brake = keys[K_SPACE]

    def _parse_vehicle_wheel(self):
        numAxes = self._joystick.get_numaxes()
        #print(self._joystick)
        #print(numAxes)
        jsInputs = [float(self._joystick.get_axis(i)) for i in range(numAxes)]
        #print(jsInputs)
        jsButtons = [float(self._joystick.get_button(i)) for i in
                     range(self._joystick.get_numbuttons())]
        #print(jsButtons)

        # Custom function to map range of inputs [1, -1] to outputs [0, 1] i.e 1 from inputs means nothing is pressed
        # For the steering, it seems fine as it is
        K1 = 0.25  #default was 1.0 # 0.55 
        steerCmd = K1 * math.tan(1.1 * jsInputs[self._steer_idx])

        K2 = 1.6  # 1.6
        throttleCmd = K2 + (2.05 * math.log10(
            -0.7 * jsInputs[self._throttle_idx] + 1.4) - 1.2) / 0.92
        if throttleCmd <= 0:
            throttleCmd = 0
        elif throttleCmd > 1:
            throttleCmd = 1

        brakeCmd = 1.6 + (2.05 * math.log10(
            -0.7 * jsInputs[self._brake_idx] + 1.4) - 1.2) / 0.92
        if brakeCmd <= 0:
            brakeCmd = 0
        elif brakeCmd > 1:
            brakeCmd = 1

        self._control.steer = steerCmd
        self._control.brake = brakeCmd
        self._control.throttle = throttleCmd

        #toggle = jsButtons[self._reverse_idx]

        self._control.hand_brake = bool(jsButtons[self._handbrake_idx])

    def _parse_walker_keys(self, keys, milliseconds):
        self._control.speed = 0.0
        if keys[K_DOWN] or keys[K_s]:
            self._control.speed = 0.0
        if keys[K_LEFT] or keys[K_a]:
            self._control.speed = .01
            self._rotation.yaw -= 0.08 * milliseconds
        if keys[K_RIGHT] or keys[K_d]:
            self._control.speed = .01
            self._rotation.yaw += 0.08 * milliseconds
        if keys[K_UP] or keys[K_w]:
            self._control.speed = 5.556 if pygame.key.get_mods() & KMOD_SHIFT else 2.778
        self._control.jump = keys[K_SPACE]
        self._rotation.yaw = round(self._rotation.yaw, 1)
        self._control.direction = self._rotation.get_forward_vector()

    @staticmethod
    def _is_quit_shortcut(key):
        return (key == K_ESCAPE) or (key == K_q and pygame.key.get_mods() & KMOD_CTRL)

```

## IV.) Configure the sensitivity of your Steering_Wheel

You can modify the function _parse_vehicle_wheel() in the class mentioned above to change the sensitivity of your wheel configurations.

For example to change sensitivity of you steering just set the K1 parameter higher or lower. Per default the value was 1.0 and we set it to 0.25 for a better driving comfort.

Further possible modifications could be done for the throttle and brake sensitivity.

```
 def _parse_vehicle_wheel(self):
        numAxes = self._joystick.get_numaxes()
        #print(self._joystick)
        #print(numAxes)
        jsInputs = [float(self._joystick.get_axis(i)) for i in range(numAxes)]
        #print(jsInputs)
        jsButtons = [float(self._joystick.get_button(i)) for i in
                     range(self._joystick.get_numbuttons())]
        #print(jsButtons)

        # Custom function to map range of inputs [1, -1] to outputs [0, 1] i.e 1 from inputs means nothing is pressed
        # For the steering, it seems fine as it is
        K1 = 0.25  #default was 1.0 # 0.55 
        steerCmd = K1 * math.tan(1.1 * jsInputs[self._steer_idx])

        K2 = 1.6  # 1.6
        throttleCmd = K2 + (2.05 * math.log10(
            -0.7 * jsInputs[self._throttle_idx] + 1.4) - 1.2) / 0.92
        if throttleCmd <= 0:
            throttleCmd = 0
        elif throttleCmd > 1:
            throttleCmd = 1

        brakeCmd = 1.6 + (2.05 * math.log10(
            -0.7 * jsInputs[self._brake_idx] + 1.4) - 1.2) / 0.92
        if brakeCmd <= 0:
            brakeCmd = 0
        elif brakeCmd > 1:
            brakeCmd = 1

        self._control.steer = steerCmd
        self._control.brake = brakeCmd
        self._control.throttle = throttleCmd

        #toggle = jsButtons[self._reverse_idx]

        self._control.hand_brake = bool(jsButtons[self._handbrake_idx])
```

## V.) Execute the CARLA Scenario Runner with your Steering Wheel

Finally, you can execute (from the scenario runner directory) the Scenario Runner with your individually configured steering wheel:

```
python manual_control_steering_wheel.py
```