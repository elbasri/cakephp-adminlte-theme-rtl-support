# CakePHP AdminLTE Theme (1.1.0) with RTL Support (ARABIC AdminLTE)
# تعريب لوحة القيادة AdminLTE



### للتحميل والتثبيت

لتحميل عميل الملحن: [composer](http://getcomposer.org).

أمر التحميل

```
composer require nacer/cakephp-adminlte-rtl
```

**النص الأصلي لكيفية التثبيت في المكتبة البرمجية CAKEPHP 3**

### Enable Plugin

```php
// src/Application.php

public function bootstrap()
{
    $this->addPlugin('AdminLTE');
}
```

Before of CakePHP 3.7

```php
// config/bootstrap.php

Plugin::load('AdminLTE', ['bootstrap' => true, 'routes' => true]);
```

### Enable Theme

```php
// src/Controller/AppController.php

public function beforeRender(Event $event)
{
    $this->viewBuilder()->setTheme('AdminLTE');

    // Before of CakePHP 3.5
    $this->viewBuilder()->theme('AdminLTE');
}
```

### Enable Form

```php
// src/View/AppView.php

public function initialize()
{
    $this->loadHelper('Form', ['className' => 'AdminLTE.Form']);
}
```

### Configure

```php
// new config/adminlte.php file

return [
    'Theme' => [
        'title' => 'AdminLTE',
        'logo' => [
            'mini' => '<b>A</b>LT',
            'large' => '<b>Admin</b>LTE'
        ],
        'login' => [
            'show_remember' => true,
            'show_register' => true,
            'show_social' => true
        ],
        'folder' => ROOT,
        'skin' => 'blue'
    ]
];

// config/bootstrap.php

Configure::load('adminlte', 'default');
```

Before of CakePHP 3.7

```php
// config/bootstrap.php

Configure::write('Theme', [
    'title' => 'AdminLTE',
    'logo' => [
        'mini' => '<b>A</b>LT',
        'large' => '<b>Admin</b>LTE'
    ],
    'login' => [
        'show_remember' => true,
        'show_register' => true,
        'show_social' => true
    ],
    'folder' => ROOT,
    'skin' => 'blue' // default is 'blue'
]);
```

# Customize Layout

If you want to [Customize Layout](https://github.com/maiconpinto/cakephp-adminlte-theme/wiki/Customize-Layout)

# What's the features

### Layouts

There are 10 layout files.

- boxed
- collapsed
- default **it's the main layout**
- documentation
- fixed
- lockscreen
- login
- print
- register
- top

### View Blocks

There are 3 Blocks where you can extend your theme.

- **css**

```php
<?php echo $this->fetch('css'); ?>
```

One example is `src/Template/Pages/home.ctp`:

```php
<?php echo $this->Html->css('AdminLTE./bower_components/morris.js/morris', ['block' => 'css']); ?>
```

- **script**

```php
<?php echo $this->fetch('script'); ?>
```

One example is `src/Template/Pages/home.ctp`:

```php
<?php echo $this->Html->script('AdminLTE./bower_components/morris.js/morris.min', ['block' => 'script']); ?>
```

- **scriptBottom**

```php
<?php echo $this->fetch('scriptBottom'); ?>
```

One example is `src/Template/Pages/home.ctp`:

```php
<?php $this->start('scriptBottom'); ?>
    <script>
      $.widget.bridge('uibutton', $.ui.button);
    </script>
<?php  $this->end(); ?>
```

### Elements

There are 7 element files.

- Element/
    - aside/
        - form
        - sidebar-menu
        - user-panel
    - aside-control-sidebar
    - aside-main-sidebar
    - footer
    - nav-top

### Flash Message

The theme is prepared to show Flash Messages.

```php
<?php echo $this->Flash->render(); ?>
<?php echo $this->Flash->render('auth'); ?>
```

### Bake

One of the better Cake features. The theme is prepared to use Bake. 

```
bin/cake bake all user --theme AdminLTE
```

### View

- **AdminLTEView**

This is one the better theme feature. It change the pattern how Cake show view files.

Basically, you overwrite any theme, plugin and prefix files.

1. src/Template/Plugin/$theme/Plugin/$plugin/$prefix/
2. src/Template/Plugin/$theme/Plugin/$plugin/
3. src/Template/Plugin/$theme/$prefix/
4. src/Template/Plugin/$theme/

### FormHelper

FormHelper by default has format template based on Foundation template. This helper overwrite these templates.

### Behavior

- **DatepickerBehavior**

When you configure `App.defaultLocale` to `pt_BR` this Behavior is util.

### Locale

When you configure `App.defaultLocale` to `pt_BR` this Locale is util.

### Page debug

Added link to default page of CakePHP.

![Page debug](docs/page-debug.png)

# Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Add some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
