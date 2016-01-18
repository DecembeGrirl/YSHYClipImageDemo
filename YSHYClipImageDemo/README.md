# YSHYClipImageDemo
图片裁剪
借助imagePickerController来实现的

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
    //    clipView.scaleRation = 2;// 图片缩放的最大倍数 默认为3
    [picker pushViewController:clipView animated:YES];
    
  }

    #pragma mark - ClipViewControllerDelegate
    -(void)ClipViewController:(YSHYClipViewController *)clipViewController FinishClipImage:(UIImage *)editImage
    {
       [clipViewController dismissViewControllerAnimated:YES completion:^{
         [btn setImage:editImage forState:UIControlStateNormal];
        }];;
    }

    效果图
![image](https://github.com/DecembeGrirl/YSHYClipImageDemo/blob/master/ClipViewController/YHSYClipImage.gif)
有任何疑问,建议或者意见 都要告诉我哦~
