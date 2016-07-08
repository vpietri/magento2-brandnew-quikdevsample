QuickDevBar sample extension
====================================

## About

This sample module **BrandNew_QuikDevSample** explain how to extend [ADM_QuickDevBar](https://github.com/vpietri/magento2-developer-quickdevbar)

## Basic module files

- registration.php
```php
\Magento\Framework\Component\ComponentRegistrar::register(
    \Magento\Framework\Component\ComponentRegistrar::MODULE,
    'BrandNew_QuikDevSample',
    __DIR__
);
```

- etc/module.xml
```xml
<?xml version="1.0" encoding="UTF-8"?>
<config xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:noNamespaceSchemaLocation="../../../../../lib/internal/Magento/Framework/Module/etc/module.xsd">
   <module name="BrandNew_QuikDevSample" setup_version="0.1.1"/>
   <depends>
   </depends>
   <sequence>
        <module name="ADM_QuickDevBar" />
   </sequence>
</config>
```

## Layout

- view/base/layout/default.xml

### Main tab
Declare a main tab "New" just before "Help" tab (qdb.tab.help)

```xml
      <referenceBlock name="quick.dev.maintabs">
        <block class="ADM\QuickDevBar\Block\Tab\Wrapper" name="qdb.tab.new.tab" before="qdb.tab.help" template="tabs.phtml">
            <action method="setTitle">
              <argument name="title" xsi:type="string">New</argument>
            </action>
        </block>   
      </referenceBlock>
```


### Sub tab (static)
Declare a sub tab in main tab "Info" (qdb.tab.info)

We are using external class so we hav to prefix template file with our module name **BrandNew_QuikDevSample**::subtab/lorem.phtml
```xml
      <referenceBlock name="qdb.tab.info">
        <block class="ADM\QuickDevBar\Block\Tab\Panel" name="qdb.tab.info.lorem.subtab" after="-" template="BrandNew_QuikDevSample::subtab/lorem.phtml">
            <action method="setTitle">
              <argument name="title" xsi:type="string">New Sub Tab</argument>
            </action>                    
        </block>      
      </referenceBlock>
```


