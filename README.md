# mbed-netsocket-tests
Tests mbed network stack compatibility

# Running the tests

In an mbed-os project...

1. `cd mbed-os`
2. `mbed update latest`
3. `cd TESTS`
2. `git clone https://github.com/sarahmarshy/nsapi`
3. Create a `json` file and copy into it the contents of [ethernet.json](https://github.com/sarahmarshy/nsapi/blob/master/netsocket/ethernet.json).
4. Change [this line](https://github.com/sarahmarshy/nsapi/blob/master/netsocket/ethernet.json#L5) in your `json` file to match your `NetworkInterface` header file.
5. Change [this line](https://github.com/sarahmarshy/nsapi/blob/master/netsocket/ethernet.json#L8) in your `json` file to match how you construct your `NetworkInterface`.
6. Change [this line](https://github.com/sarahmarshy/nsapi/blob/master/netsocket/ethernet.json#L12) in your `json` file to match how you would use your `NetworkInterface` to connect to a network. You must leave the variable name as `net`.
7. If your `NetworkInterface` driver is not part of the project, add it.
8. Remove any `main.cpp` in the root of your project directory
8. In the root of you project run: `mbed test -t [toolchain] -m [mcu] -n mbed-os-tests-nsapi-* --app-config path/to/your/json/file`
