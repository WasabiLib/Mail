Wasabi Mail Module for Zend Framework 2
=======================================================

#Configuration
The Mail Module is configured as a service and registered to the service manager.
You have 3 default *env*-types for configuration in vendor/WasabiMail/config.php:
 
1. **local** - sended emails are saved as text files in vendor/WasabiMail/localMails
2. **develop** - for staging or development servers. It is supposed that a Mail-Server is accessible. Emails are sended to the given address in the config.php
3. **production** - The transporter is SendMail. This can only be changed in the Module.php

You can change this behavior in the Module.php if necessary.


#Examples

##Simple Usage
    $mail = $this->getServiceLocator()->get("Mail");
    $mail->setBody("Hello World");
    $mail->setTo("recipient@domain.com");
    $mail->send();

##Using  Html Templates
Using a template for sending emails is based on the ViewModel approach of ZF2. You only need to create a new
ZF2 *ViewModel* instance, set your template, fill in your variables and pass it to the setBody method of the Mail Module.

**WasabiMail is bundled with a *responsive* Html Email-Template that you can customize for your own needs.**
This template is tested with common email clients like Microsoft Outlook or Google Mail.
    
    $mail = $this->getServiceLocator()->get("Mail");
    $viewModel = new ViewModel();
    $viewModel->setTemplate("responsive");
    $mail->setBody($viewModel);
    $mail->send();

The template path stack is set to WasabiMail/templates. If necessary you can change this in the config.php 

