# mbed-netsocket-tests
Tests mbed network stack compatibility

# Running the tests

1. Create a new mbed-os project: `mbed new empty-project`
2. `cd mbed-os`
3. `mbed update latest`
4. `cd TESTS`
5. `git clone https://github.com/sarahmarshy/nsapi`
6. Create a `json` file and copy into it the contents of [network.json](/blob/master/network.json).
7. Change the ["header-file"](/blob/master/network.json#L5) value in your `json` file to match your `NetworkInterface` header file.
   * For example, `"\"ESP8266Interface.h\""`
8. Change the ["object-construction"](/blob/master/network.json#L8) value in your `json` file to match how you construct your `NetworkInterface`.
   * For example, `"new ESP8266Interface(D1, D0)"`
9. Change the ["connect-statement"](/blob/master/network.json#L12) value in your `json` file to match how you would use your `NetworkInterface` to connect to a network. You must leave the variable name as `net`.
   * For example, `"((ESP8266Interface *)net)->connect(\"SSID\", \"Password\", NSAPI_SECURITY_WPA_WPA2)"`
10. If your `NetworkInterface` driver is not part of the project, add it.
11. Remove any `main.cpp` in the root of your project directory
12. In the root of your project run: `mbed test -t [toolchain] -m [mcu] -n mbed-os-tests-nsapi-* --app-config path/to/your/json/file`
