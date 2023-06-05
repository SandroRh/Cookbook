# Instantly Identify the Magento 2 Template File You Are Looking For

Source: https://jamersan.com/instantly-identify-magento-2-template-file-looking/

Magento 2 out-of-the-box comes with over 60,000 files/folders. If you are updating a page on the frontend, sometimes the location of the template file you are editing is obvious; other times it can be elusive.

In following, I will share with you an arsenal of techniques to find whatever you need to know about the block you want to edit. These techniques will reveal many helpful details pertaining to a block such as – but not limited to – the full path of the template file, its class, block name, parent block, and children. Sometimes, after perusing xml files, it’s hard to be certain we have correctly identified such details. The technique will allow us to be certain.

First, ensure you have xDebug installed and enabled.

Second, identify the part of the page you want to edit. Let’s determine what block and template file display the “Contact Information” on the customer dashboard shown below. To do this, find a word – or phrase – that only appears once on the page. The email address (testguyadmin@nga.com) is displayed only once so let’s use that.

Third, we need to set a debugging breakpoint in our IDE. The picture below shows a breakpoint inside of the toHtml function in the class called Magento\Framework\View\Element\AbstractBlock. Place your breakpoint at this location (see picture below).

Now, we need to apply a “condition” to our breakpoint. A condition is an expression and the debugger will not stop at the breakpoint unless this expression evaluates to true. The picture below shows a box that appears when we place our cursor on the same line as the breakpoint and then press “command + shift + F8” if your on a mac, or “ctrl + shift + F8” if your on windows. In this box, type in the following text on the blue line: “strpos($html,’theWordsYouAreLookingFor’) > 0”. Then, press the “Done” button at the bottom right corner of the box.

Ensure that xDebug is active and then reload the customer account page. Now, as the image below illustrates, the debugger will stop at this breakpoint when the block that contains the text we entered is being rendered. This technique works because almost every single block in Magento is rendered using this code.

Now, press “alt + F8” (ou utilize a aba Console), which will open a dialogue box where you can enter in an expression. The bullet points below list several expressions that will reveal helpful information. Before doing each bullet, you must first press “alt + F8” otherwise it will not work.

- To retrieve the full path of the template file, type in “$this-> getTemplateFile()” and then press enter. The full path is: “vendor/magento/module-customer/view/frontend/templates/account/ dashboard/info.phtml”.
- To find the block’s class name, type “get_class($this)” and hit enter. The class name is: “Magento\Customer\Block\Account\Dashboard\Info”
- To determine the block’s name in the layout xml, type “$this->getNameInLayout ()” which is “customer_account_dashboard_info”.
- To determine the name of the parent block, type in “$this->getParentBlock()”. In this case, it returns false because this block has no parent; it is a top-level block, which is helpful to know. If it did have a parent, it would return that block.
- To find a list of child blocks, “$this->getChildNames()”.
- To retrieve the object of any block on the page, type “$this->getLayout()->getBlock(‘nameOfBlock)”
  Great, now you are equipped with some powerful debugging techniques for uncovering information about the blocks and template files you are editing!