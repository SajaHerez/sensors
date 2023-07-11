# sensors

any device has built-in sensors to measure orientation, motion or other environmental conditions with a very high accuracy. To monitor the three-dimensional data the device
 you can use the official [`sensors_plus`](https://pub.dev/packages/sensors_plus) package.

Flutter plugin to access the accelerometer, gyroscope, and magnetometer sensors.

Add `sensors_plus` as a dependency in your pubspec.yaml file.

This will expose such classes of sensor events through a set of streams:

- `UserAccelerometerEvent` describes the acceleration of the device, in m/$s^2$ If the device is still, or is moving along a straight line at constant speed, the reported acceleration is zero. If the device is moving e.g. towards north and its speed is increasing, the reported acceleration is towards north; if it is slowing down, the reported acceleration is towards south; if it is turning right, the reported acceleration is towards east. The data of this stream is obtained by filtering out the effect of gravity from `AccelerometerEvent`.

- `AccelerometerEvent` describes the acceleration of the device, in m/$s^2$, including the effects of gravity. Unlike `UserAccelerometerEvent`, this stream reports raw data from the accelerometer (physical sensor embedded in the mobile device) without any post-processing. The accelerometer is unable to distinguish between the effect of an accelerated movement of the device and the effect of the surrounding gravitational field. This means that, at the surface of Earth, even if the device is completely still, the reading of `AccelerometerEvent` is an acceleration of intensity 9.8 directed upwards (the opposite of the graviational acceleration). This can be used to infer information about the position of the device (horizontal/vertical/tilted). `AccelerometerEvent` reports zero acceleration if the device is free falling.

- `GyroscopeEvent` describes the rotation of the device.
- `MagnetometerEvent` describes the ambient magnetic field surrounding the device. A compass is an example usage of this data.

These events are exposed through a `BroadcastStream`: `accelerometerEvents`, `userAccelerometerEvents`, `gyroscopeEvents`, and `magnetometerEvents`, respectively.

![https://www.youtube.com/watch?v=Fq5zNPJufD0]()
