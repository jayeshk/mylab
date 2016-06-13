#evo-plugin-ios

### Steps to prepare plugin source code

Create folder structure as below - 
--plugin.xml
--source/
--www/


Create plugin.xml file which will keep information about plugin and dependency

See this guide for more information about Plugin.xml

#####Create plugin.xml

[Plugin.xml](https://cordova.apache.org/docs/en/latest/plugin_ref/spec.html)

#####Collect source

Once plugin development is done, collect all source files (.h/.m) and depency files and frameworks. Add source files under 'source' folder.
Collect all *.js & *.html (if any) files and add them to 'www' folder. These two folders will be copied while plugin is installed.
Following are example entris in plugin.xml

```xml
<header-file src="src/ios/EVOSwiper.h"/>
<source-file src="src/ios/EVOSwiper.m"/>
```

```xml
<js-module name="EVOSwiper" src="www/EVOSwiper.js">
<clobbers target="EVOSwiper"/>
</js-module>
```

#####Link frameworks and dependency

For cordova plugin add following framework dependency which may need while plugin it installded and compiled.

Link Commerence Drive framework
```xml
<framework custom="true" src="src/ios/framework/EVOCommerceDriver-ITM100.framework" />
```

Add other system frameworks required by Commerce driver.

```xml
<framework src="AVFoundation.framework" weak="true"/>
<framework src="UIKit.framework" weak="true"/>
<framework src="Security.framework" weak="true"/>
<framework src="ExternalAccessory.framework" weak="true"/>
<framework src="AudioToolbox.framework" weak="true"/>
<framework src="MediaPlayer.framework" weak="true"/>
<framework src="CoreBluetooth.framework" weak="true"/>
<framework src="MessageUI.framework" weak="true"/>
<framework src="libstdc++.tbd" weak="true"/>
<framework src="libxml2.2.tbd" weak="true"/>
```

*Ideally plugin should be hosted on repository once it is stable and fully developed, also it can be also installed by manually downloading source as mention in this process.*
See [Plugin installation guide](./pluginsetup.md)