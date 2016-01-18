# YSHYClipImageDemo
图片裁剪

基于imagePickerController 实现圆形 方形两种方式的图片裁剪,支持自定义裁剪大小,支持自定义图片缩放比例

#pragma mark - imagePickerControllerDelegate
-(void)imagePickerController:(UIImagePickerController *)picker didFinishPickingMediaWithInfo:(NSDictionary<NSString *,id> *)info
{
    UIImage * image = info[@"UIImagePickerControllerOriginalImage"];
    
    YSHYClipViewController * clipView = [[YSHYClipViewController alloc]initWithImage:image];
    clipView.delegate = self;
    clipView.clipType = clipType; //支持圆形:CIRCULARCLIP 方形裁剪:SQUARECLIP   默认:圆形裁剪
    if(![textField.text isEqualToString:@""])
    {
        radius =textField.text.intValue;
        clipView.radius = radius;   //设置 裁剪框的半径  默认120
    }
    //    clipView.scaleRation = 5;// 图片缩放的最大倍数 默认为10
    [picker pushViewController:clipView animated:YES];
    
}

#pragma mark - ClipViewControllerDelegate
-(void)ClipViewController:(YSHYClipViewController *)clipViewController FinishClipImage:(UIImage *)editImage
{
      [clipViewController dismissViewControllerAnimated:YES completion:^{
          [btn setImage:editImage forState:UIControlStateNormal];
      }];;
}


![image](https://github.com/DecembeGrirl/YSHYClipImageDemo/blob/master/YSHYClipImageDemo/ClipViewController/YHSYClipImage.gif)
