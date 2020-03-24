# Header
常用宏定义

//屏幕尺寸
#define SCREENH      [UIScreen mainScreen].bounds.size.height
#define SCREENW      [UIScreen mainScreen].bounds.size.width

#define kSTATUS_H    ([[UIApplication sharedApplication] statusBarFrame].size.height>20?44:20) // 适配刘海屏状态栏
#define kTABBAR_H    ([[UIApplication sharedApplication] statusBarFrame].size.height>20?83:49) // 适配刘海屏底栏高度
#define kBOTTOM_H    ([[UIApplication sharedApplication] statusBarFrame].size.height>20?34:0)  // 适配刘海屏底部多出来的高度

//----------------判断当前的iPhone设备/系统版本---------------
// 判断是否为iPhone
#define IS_IPHONE   (UI_USER_INTERFACE_IDIOM() == UIUserInterfaceIdiomPhone)
// 判断是否为iPad
#define IS_IPAD     (UI_USER_INTERFACE_IDIOM() == UIUserInterfaceIdiomPad)
// 判断是否为ipod
#define IS_IPOD     ([[[UIDevice currentDevice] model] isEqualToString:@"iPod touch"])

//----------------判断系统版本---------------
// 获取系统版本
#define IOS_SYSTEM_VERSION [[[UIDevice currentDevice] systemVersion] floatValue]
// 判断 iOS 8 或更高的系统版本
#define IOS_VERSION_8_OR_LATER (([[[UIDevice currentDevice] systemVersion] floatValue] >=8.0)? (YES):(NO))
// 判断 iOS 10 或更高的系统版本
#define IOS_VERSION_10_OR_LATER (([[[UIDevice currentDevice] systemVersion] floatValue] >=10.0)? (YES):(NO))

//----------------判断机型 根据尺寸---------------
// 判断是否为 iPhone 4/4S - 3.5 inch
#define iPhone4_4S [[UIScreen mainScreen] bounds].size.width == 320.0f && [[UIScreen mainScreen] bounds].size.height == 480.0f
// 判断是否为 iPhone 5/5SE - 4.0 inch
#define iPhone5_5SE [[UIScreen mainScreen] bounds].size.width == 320.0f && [[UIScreen mainScreen] bounds].size.height == 568.0f
// 判断是否为iPhone 6/6S/7/8 - 4.7 inch
#define iPhone6_6S [[UIScreen mainScreen] bounds].size.width == 375.0f && [[UIScreen mainScreen] bounds].size.height == 667.0f
// 判断是否为iPhone 6Plus/6SPlus/7P/8P - 5.5 inch
#define iPhone6Plus_8Plus [[UIScreen mainScreen] bounds].size.width == 414.0f && [[UIScreen mainScreen] bounds].size.height == 736.0f
// 判断是否为iPhoneX - 5.8 inch
#define iPhoneX ([UIScreen instancesRespondToSelector:@selector(currentMode)] ? CGSizeEqualToSize(CGSizeMake(1125, 2436), [[UIScreen mainScreen] currentMode].size) : NO)
// 判断是否为iPhoneXS - 5.8 inch
#define iPhoneXS ([UIScreen instancesRespondToSelector:@selector(currentMode)] ? CGSizeEqualToSize(CGSizeMake(1125, 2436), [[UIScreen mainScreen] currentMode].size) : NO)
// 判断是否为iPhoneXR - 6.1 inch
#define iPhoneXR ([UIScreen instancesRespondToSelector:@selector(currentMode)] ? CGSizeEqualToSize(CGSizeMake(828, 1792), [[UIScreen mainScreen] currentMode].size) : NO)
// 判断是否为iPhoneXS MAX - 6.5 inch
#define iPhoneXSMax ([UIScreen instancesRespondToSelector:@selector(currentMode)] ? CGSizeEqualToSize(CGSizeMake(1242, 2688), [[UIScreen mainScreen] currentMode].size) : NO)

// 主要是用于区分是否是 刘海屏
#define LiuHaiPhone \
({BOOL isLiuHaiPhone = NO;\
if (@available(iOS 11.0, *)) {\
isLiuHaiPhone = [[UIApplication sharedApplication] delegate].window.safeAreaInsets.bottom > 0.0;\
}\
(isLiuHaiPhone);})


#define EMKeyWindow                         [UIApplication sharedApplication].delegate.window


//屏幕宽度适配 - 比例
#define WidthScale                          [UIScreen mainScreen].bounds.size.width/375
//屏幕高度适配 - 比例
#define HeightScale                         [UIScreen mainScreen].bounds.size.height/667

//适配屏幕宽度
#define FitWidth(x)                         (x)/2.0*(ISIPAD ? 1.3 : WidthScale)
//适配屏幕高度
#define FitHeight(y)                        (y)/2.0*(ISIPAD ? 1.3 : HeightScale)
//根据字体大小适配大小
#define FitFont(px)                         (px)/96.0*72.0

//获取状态栏的高度 iPhone X - 44pt  其他20pt
#define StatusBarHeight                     [[UIApplication sharedApplication] statusBarFrame].size.height

//获取导航栏的高度 - （不包含状态栏高度） 44pt
#define NavigationBarHeight                 self.navigationController.navigationBar.frame.size.height

//屏幕底部  tabBar高度49pt + 安全视图高度34pt(iPhone X)
#define TabbarHeight                        self.tabBarController.tabBar.frame.size.height

//屏幕顶部 导航栏高度（包含状态栏高度）
#define NavigationHeight                    (StatusBarHeight + NavigationBarHeight)

//屏幕底部安全视图高度 - 适配iPhone X底部
#define TOOLH                               ((ISIPHONEX || ISIPHONEXR_XSMAX) ? 34 : 0)

//屏幕底部  toolbar高度 + 安全视图高度34pt
#define ToolbarHeight                       self.navigationController.toolbar.frame.size.height

//RBG
#define RGB(r,g,b,a)                        [UIColor colorWithRed:(double)r/255.0f green:(double)g/255.0f blue:(double)b/255.0f alpha:a]

//字体
#define FONT_SIZE(fontSize)                 [UIFont systemFontOfSize:fontSize]


//---------------Colour-------------------
// 设置随机颜色
#define RandomColor [UIColor colorWithRed:arc4random_uniform(256)/255.0 green:arc4random_uniform(256)/255.0 blue:arc4random_uniform(256)/255.0 alpha:1.0]
// 设置RGB颜色/设置RGBA颜色
#define RGBAColor(r, g, b, a)  [UIColor colorWithRed:r/255.0f green:g/255.0f blue:b/255.0f alpha:a]
#define RGBColor(r, g, b)      [UIColor colorWithRed:r/255.0f green:g/255.0f blue:b/255.0f alpha:1.0f]
// 十六进制数值 eg:@"#3499DB"
#define HEXAColor [UIColor colorFromHexString: hexValue]
#define HEXColor(hexValue) [UIColor colorWithRed:((float)((hexValue & 0xFF0000) >> 16)) / 255.0 green:((float)((hexValue & 0xFF00) >> 8)) / 255.0 blue:((float)(hexValue & 0xFF)) / 255.0 alpha:1.0f]

//分割线边距 UITableView
#define separator_Inset                      UIEdgeInsetsMake(0, 15, 0, 15)

#define EMUserDefault                       [NSUserDefaults standardUserDefaults]
#define EMUserNotify                        [NSString stringWithFormat:@"%@-notify",[EMUserDefault objectForKey:@"username"]]

//循环引用
#define WeakSelf(weakSelf)                  __weak __typeof(&*self)    weakSelf  = self;
#define StrongSelf(strongSelf)              __strong __typeof(&*self) strongSelf = weakSelf;

//token
#define EMToken                               [[NSUserDefaults standardUserDefaults] objectForKey:@"EMToken"]

//系统弹窗
#define ALERTVIEW(_TITLE_,_MESSAGE_)        UIAlertView *alert = [[UIAlertView alloc]initWithTitle:_TITLE_ message:_MESSAGE_ delegate:nil cancelButtonTitle:nil otherButtonTitles:@"确定", nil];\
[alert show];



//--------------沙盒目录文件路径---------------
// 获取沙盒主目录路径
#define SBPath_Home = NSHomeDirectory();
//获取沙盒 Document
#define SBPath_Document [NSSearchPathForDirectoriesInDomains(NSDocumentDirectory, NSUserDomainMask, YES) firstObject]
//获取沙盒 Library
#define SBPath_Library  [NSSearchPathForDirectoriesInDomains(NSLibraryDirectory, NSUserDomainMask, YES) lastObject];
//获取沙盒 Cache
#define SBPath_Cache    [NSSearchPathForDirectoriesInDomains(NSCachesDirectory, NSUserDomainMask, YES) firstObject]
//获取temp
#define SBPath_Temp NSTemporaryDirectory()

//-------------- NSLog在release下不输出 ---------------
#ifndef __OPTIMIZE__
#define NSLog(...) NSLog(__VA_ARGS__)
#else
# define NSLog(...) {}
#endif
