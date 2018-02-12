reCAPTCHA is a CAPTCHA-like system designed to establish that a computer user is human (normally in order to protect websites from bots) and, at the same time, assist in the digitization of books

Here I am describe how can add google captcha in yii1 MVC frame work.

YiiReCaptcha 
============
Based on reCaptcha API 2.0

## Quick Start

You can clone the [github repo](https://github.com/jafarkhanphp/googleRcaptcha.git) and get the full codebase to build the distributive something you want. 

## Installation
* 1/ Download GitHub repo (dakiquang/yiiReCaptcha) and extract files into a destination folder(extensionsfolder or any folder in your structure)

* 2/ [Sign up for an reCAPTCHA API keys on Google reCaptcha](https://www.google.com/recaptcha/admin#createsite). and get the key/secret pair

* 3/ Configure this component in your configuration file (main.php file). The parameters siteKey and secret are required.

//Insert code in components array()
```
'reCaptcha' => array(
		        'name' => 'reCaptcha',
		        'class' => 'application.extensions.yiiReCaptcha.ReCaptcha',
		        'key' => '6LchyUUUAAAAAHTmZYX0L3i4I9iqF23PuUSXDXDp',
		        'secret' => '6LchyUUUAAAAAIDFAhVxmp2ugfkS_3In9v02xeRZ',
		    ),

```
4/ Add `ReCaptchaValidator` in your model, for example:

    public $verifyCode;

    public function rules()
    {
        return array(
            array('verifyCode', 'required'),
            array('verifyCode', 'application.extensions.yiiReCaptcha.ReCaptchaValidator'),
        );
    }


5/ Usage this widget in your view
````
<?php
$this->widget('application.extensions.yiiReCaptcha.ReCaptcha', array(
    'model'     => $model,
    'attribute' => 'verifyCode',
));
?>
```

END.
