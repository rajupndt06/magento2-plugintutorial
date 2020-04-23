# magento2-plugintutorial

A plugin, or interceptor, is a class that modifies the behavior of public class functions
by intercepting a function call and running code before, after, or around that function call. 
This allows you to substitute or extend the behavior of original, public methods for any 
class or interface.

Extensions that wish to intercept and change the behavior of a public method can
 create a Plugin class.

In Magento2 we can create and use three types of Plugin.
1.Before listener Plugin
2.After listener Plugin
3.Around listener Plugin

Limitations

Plugins can not be used on following:

1.Final methods
2.Final classes
3.Non-public methods
4.Class methods (such as static methods)
5.__construct
6.Virtual types
7.Objects that are instantiated before Magento\Framework\Interception is bootstrapped
 
To understand more about plugin we will do a practice.

Lets do this practically, you need to follow step by step

Step 1: Create a new module called Techone_PluginTutorial
- Create the namespace Techone in the path app\code.
- Create the module name PluginTutorial in the path app\code\Techone.
- Create the file named registration.php in the path app\code\Techone\PluginTutorial
- Create the file name module.xml in the path app\code\Techone\PluginTutorial\etc

End of step #1, I have been completed the step to create new module called Techone_PluginTutorial

Step 2: Declaring a plugin
- A plugin for class object is declared in the di.xml file in the module.
- Create the new file named di.xml in the path app\code\Techone\PluginTutorial\etc\frontend
I put the di.xml file in the folder named frontend, because I want these codes only to apply
on the storefront.

You must specify these elements:
- type name. A class or interface which the plugin observes.
- plugin name. An arbitrary plugin name that identifies a plugin.
 Also used to merge the configurations for the plugin.
- plugin type. The name of a plugin’s class or its virtual type. Use the following naming 
convention when you specify this element: \Vendor\Module\Plugin\<ClassName>.

Step 3: Defining a plugin
- A pugin is used to extend or modify a public method's behaviour by applying code
before, after, or around that observed method.
- In this practice, I use the Before method
- Create a new file named Cart.php in the path app\code\Techone\PluginTutorial\Model\Cart

Before listener is called by adding prefix 'before' to the method name and setting first letter
 of original method to capital.Now method addProduct will become beforeAddProduct.

The before listener methods do not need to have a return value.
Here we are changing parameters. We set quantity to 10. 
Now it will always add 10 quantities of the product whenever we add product to cart.
So we will use before listener when we want to change parameter of an method.


Step 4: Test and see the results
Run the command lines following:
- php bin/magento setup:upgrade --keep-generated
- php bin/magento cache:flush
Go to the product page detail.


Youtube link to watch video : https://youtu.be/1eFj79Z9aHI 



