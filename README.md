# clang_api
  存取bundle中的资源，读取本地化文本，执行选择器和UserDefaults的相关操作，调用通知中心的相关操作等。

# 使用说明
 1.获取bundle资源文件路径
```ObjC
NSString *path = clang_path_for_resource_from_bundle(@"Info", @"plist", nil, @"Test");
NSLog(@"Info.plist's path: %@", path);
NSLog(@"Info.plist's content: %@", [NSDictionary dictionaryWithContentsOfFile:path]);
```

 2.获取bundle中的图片
```ObjC
UIImage *image = clang_load_image_from_bundle(@"angle-mask", @"angle-mask.bundle", @"Test");
NSLog(@"Image: %@", image);
```
	
 3.获取bundle中的图片，不缓存内存
```ObjC
UIImage *image2 = clang_image_with_contents_of_file(@"angle-mask", nil, @"angle-mask.bundle", @"Test");
NSLog(@"Image2: %@", image2);
```

 4.获取main bundle中的资源文件路径
```ObjC
NSString *path2 = clang_path_for_resource_from_bundle(@"Info", @"plist", nil, nil);
NSLog(@"info.plist's path2: %@", path2);
NSLog(@"info.plist's content2: %@", [NSDictionary dictionaryWithContentsOfFile:path2]);
```

 5.获取main bundle中的图片，不缓存内存
```ObjC
UIImage *Image3 = clang_image_with_contents_of_file(@"angle-mask", nil, nil, nil);
NSLog(@"Image3: %@", image3);
```
	
 6.读取本地化内容
```ObjC
NSLog(@"Localized string: %@", clang_localized_string(@"Lan_network_timeout", nil, @"en", @"language", @"Test"));
```

 7.其他
```ObjC
BOOL y1 = clang_equal(@1, @3);
//NSLog(@"y1: %d", y1);
BOOL y2 = clang_equal_to_string(@"try", @"try");
//NSLog(@"y2: %d", y2);

clang_perform_selector(self, @selector(run));
clang_perform_selector_v2(self, @selector(runWithArg:), @10);
clang_delay_perform_selector(self, @selector(update), 1.0);
clang_delay_perform_selector_v2(self, @selector(updateWithArg:), @"update", 1.0);
    
clang_store_object(@"AppID", @"g7482293", YES);
NSString *appID = clang_read_object(@"AppID");
//NSLog(@"appID: %@", appID);
//clang_remove_object(@"AppID", YES);
    
clang_add_observer(self, @selector(logInWithResult:), @"DYFLoginNotification", nil);
//clang_remove_observer_v2(self, @"DYFLoginNotification", nil);
//clang_remove_observer(self);
clang_post_notification_name(@"DYFLoginNotification", @1);
clang_post_notification_name_v2(@"DYFLoginNotification", nil, @{@"ret": @0});
```
