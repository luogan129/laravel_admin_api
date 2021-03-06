# laravel5.4 后台管理


## 启动步骤

> 1 安装PHP依赖库：composer install

> 2 修改.env数据库配置信息

> 3 执行： php artisan migrate

> 4 执行： php artisan db:seed --class=PermissionSeeder

> 5 启动： php artisan serve



## 注意

> 添加操作管理的数据的时候，命名空间、类名、方法名请根据实际情况添加，不要添加不存在的命名空间、类，否则程序会报错.
当添加不存在的命名空间、类名、方法名的时候，程序在生成URL的时候会提示找不到相应的类


## 开始

浏览器打开http://localhost:8000/  进入登录界面：

用户角色：用户名/密码

管理员账号：admin/123456


## 图形验证码

`composer require mews/captcha`

`Mews\Captcha\CaptchaServiceProvider::class,`

`'Captcha' => Mews\Captcha\Facades\Captcha::class,`

`php artisan vendor:publish`  #生成config/captcha.php

## 图片处理扩展包

`composer require intervention/image`

`Intervention\Image\ImageServiceProvider::class,`

`'Image' => Intervention\Image\Facades\Image::class,`

`php artisan vendor:publish --provider="Intervention\Image\ImageServiceProviderLaravel5"`  #生成config/image.php

// 修改指定图片的大小

`$img = Image::make('images/avatar.jpg')->resize(200, 200);`

// 插入水印, 水印位置在原图片的右下角, 距离下边距 10 像素, 距离右边距 15 像素

`$img->insert('images/watermark.png', 'bottom-right', 15, 10);`

// 将处理后的图片重新保存到其他路径

`$img->save('images/new_avatar.jpg');`

// 上面的逻辑可以通过链式表达式搞定

`$img = Image::make('images/avatar.jpg')->resize(200, 200)->insert('images/new_avatar.jpg', 'bottom-right', 15, 10);`

## excel服务

`composer require "maatwebsite/excel:~2.1.0"`

`Maatwebsite\Excel\ExcelServiceProvider::class,`

`'Excel' => Maatwebsite\Excel\Facades\Excel::class,`

`php artisan vendor:publish --provider="Maatwebsite\Excel\ExcelServiceProvider"`  #生成config/excel.php

## pdf 服务

`composer require barryvdh/laravel-dompdf`

`Barryvdh\DomPDF\ServiceProvider::class,`

`'PDF' => Barryvdh\DomPDF\Facade::class,`

`php artisan vendor:publish --provider="Barryvdh\DomPDF\ServiceProvider"`  #生成config/dompdf.php

## html过滤包

`composer require mews/purifier`

`Mews\Purifier\PurifierServiceProvider::class,`

`'Purifier' => Mews\Purifier\Facades\Purifier::class,`

`php artisan vendor:publish --provider="Mews\Purifier\PurifierServiceProvider"`  #生成config/purifier.php

`clean(Input::get('inputname'));`

`Purifier::clean(Input::get('inputname'));`

## 浏览器跨域

`composer require barryvdh/laravel-cors`

`Barryvdh\Cors\ServiceProvider::class,`

`php artisan vendor:publish --provider="Barryvdh\Cors\ServiceProvider"`  #生成config/cors.php

## 根据ip获取地址位置

`composer require "zhuzhichao/ip-location-zh"`

`'Ip'  => 'Zhuzhichao\IpLocationZh\Ip::class,`

`Ip::find('171.12.10.156')` or `Ip::find(Request::getClientIp())`