# VCode
图片的验证码类，是常见的web需要功能

# Installation
    直接使用命令行
        composer require edmmss/vcode:@dev -vvv
    
    或者编辑composer.json
        在require里面加上
            "edmmss/vcode": "@dev"
        再加上
        "repositories": [
            {
                "type": "git",
                "url": "https://github.com/edmmss/VCode.git"
            }
        ]
        
        composer update edmmss/vcode -vvv
        
# demo

    <?php
    // 使用默认参数配置
    $vcode = new VCode();
    $vcode->setPm();
    
    // 获取验证码
    echo $vcode->getCode();
    // 直接输入图片
    $vcode->getImg()
    
    // 自己设置参数配置,具体有什么参数可以参考源码里面的成员属性
    $vcode = new VCode();
    $path = $vcode->getFontsPath();
    $fonts = [
        'segoescb.ttf',
        'Action_Jackson_Font_by_OhMyCraazyEditions.ttf',
        'Delicious-Bold.otf',
        'Delicious-BoldItalic.otf',
        'Delicious-Heavy.otf',
        'Delicious-Italic.otf',
        'Delicious-Roman.otf',
        'Delicious-SmallCaps.otf',
        'miso.otf',
        'MISO-BOL.OTF',
    ];

    foreach ($fonts as &$value) {
        $value = $path . $value;
    }

    $vcode->setPm([
        'count'     => 4,
        'width'     => 300,
        'height'    => 100,
        'point'     => 1.8,
        'arc'       => 1,
        'fontfiles' => $fonts,
    ]);
    
    // 获取验证码
    echo $vcode->getCode();
    // 直接输入图片
    $vcode->getImg()