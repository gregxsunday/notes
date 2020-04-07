# root ssh access on linux
```
11:00:52 ~/pentests/tools/usbmuxd-1.0.8/python-client:$ python2 tcprelay.py -t 22:2222 &
Forwarding local port 2222 to remote port 22
11:00:55 ~/pentests/tools/usbmuxd-1.0.8/python-client:$ ssh -p 2222 root@127.0.0.1
```
# Dynamic analysis
```
passionfruit
```
# Static analysis
```
sudo docker run -it -p 8000:8000 opensecurity/mobile-security-framework-mobsf:latest
```

# Files to check in
- /private/var/mobile/Containers/Data/Application/{ID}
1. All plist files
2. databases in Documents
# Debugger
* On the phone
```
ps aux | grep {APP}
debugserver localhost:1234 --attach={PID}
```
* On the Mac
```
iproxy 1234 1234
lldb
(lldb) platform select remote-ios
(lldb) process connect connect://localhost:1234
```
# Cycript
* On the phone
```
cyrun -n Runner -e
```
* On the Mac
```
./cycript -r 192.168.0.113:8556
```
# Proxy flutter

```
$ cat pfctl.txt
rdr pass inet proto tcp from 192.168.2.2 to subdomain1.domain.com port 443 -> 127.0.0.1 port 8443
rdr pass inet proto tcp from 192.168.2.2 to subdomain2.domain.com port 443 -> 127.0.0.1 port 8444
$ sudo pfctl -f pfctl.txt
$ sudo pfctl -s nat #to check the rules
```
### proxy w burpie
```
port 8443 i 8444 osobno
loopback only
adres, force TLS
support invisible
```
# Frida-gadgets

1. download frida-gadget dylib from https://github.com/frida/frida/releases and rename to eg. FridaGadget.dylib
2. create FridaGadget.config - the name must be the same as dylib file. With content:
    ```
    {
    "interaction": {
        "type": "script",
        "path": "/tmp/show-modify-method-return-value.js"
    }
    }
    ```
3. create a folder named @rpath and move a dylib file there
4. open https://github.com/Tyilo/insert_dylib in Xcode and save path of binary file
5. link dylib
    ```
    /Users/pentesty/Library/Developer/Xcode/DerivedData/insert_dylib-fahawfvwmzcchceffmydltkuutlv/Build/Products/Debug/insert_dylib \@rpath/FridaGadget.dylib Payload/Appname.app/Appname
    ```
6. 
    ```
    mv Appname_patched Appname
    cp FridaGadget.* Payload/Appname.app/Frameworks/
    zip -r "Appname INT.ipa" Payload/
    ```
7. deploy with altdeploy
8. the script on the phone in /tmp/show-modify-method-return-value.js looks like this:
```
rpc.exports = {
  init: function (stage, parameters) {
    console.log('[init]', stage, JSON.stringify(parameters));

    //Twitter: https://twitter.com/xploresec
    //GitHub: https://github.com/interference-security
    function show_modify_function_return_value(className_arg, funcName_arg)
    {
        var className = className_arg;
        var funcName = funcName_arg;
        var hook = ObjC.classes[className][funcName];
        Interceptor.attach(hook.implementation, {
          onLeave: function(retval) {
            console.log("\n[*] Class Name: " + className);
            console.log("[*] Method Name: " + funcName);
            console.log("\t[-] Type of return value: " + typeof retval);
            //console.log(retval.toString());
            console.log("\t[-] Return Value: " + retval);
            //For modifying the return value
            var newretval = ptr("0x0") //your new return value here
            retval.replace(newretval)
            console.log("\t[-] New Return Value: " + newretval)
          }
        });
    }

    //YOUR_CLASS_NAME_HERE and YOUR_EXACT_FUNC_NAME_HERE
    show_modify_function_return_value("SecurityManager" ,"+ amIDebugged")
    show_modify_function_return_value("SecurityManager" ,"+ amIJailbroken")
    show_modify_function_return_value("SecurityManager" ,"+ amIReverseEngineered")
    show_modify_function_return_value("SecurityManager" ,"+ amIRunInEmulator")
    show_modify_function_return_value("ANSMetadata" ,"- isJailbroken")
    show_modify_function_return_value("ANSMetadata" ,"- computeIsJailbroken")
    
  },
  dispose: function () {
    console.log('[dispose]');
  }
};
```

# Manually signing apps

1. Generate embedded.mobileprovision by launching the empty Xcode project - bundle name example.bundlename
2. 
    ```
    cp ~/Library/Developer/Xcode/DerivedData/<emptyappname>-<a random string>/Build/Products/Debug-iphoneos/<emptyappname>.app/embedded.mobileprovision
    ```
3. modify bundlename
    ```
    security cms -D -i embedded.mobileprovision > profile.plist
    /usr/libexec/PlistBuddy -x -c 'Print :Entitlements' profile.plist > entitlements.plist
    /usr/libexec/PlistBuddy -c "Set :CFBundleIdentifier example.bundlename" Info.plist
    ```
4. resign
    ```
    security find-identity -p codesigning -v
    codesign --force --sign "iPhone Developer: m*****************" --entitlements entitlements.plist  Payload/Plain\ Notes.app/Plain\ Notes
    ```
5. pack
    ```
    zip -qr abc.ipa Payload/
    ```
6. install 
    ```
    ideviceinstaller -i abc.ipa
    ```
**in case of the appa having binary plugins the process has to be repeated for each plugin**