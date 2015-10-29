# selecteAvatarApplication

##Feature
一个选择并显示头像圆形控件，可以通过拍照或者选择相册中的图片来设置图片

##Snapshot
![snapshot](https://github.com/zhudfly/SelectAvatarApplication/blob/master/.raw/selectAvatar.gif)

##Usage
```XML

<com.sunny.thousand.selectavatar.AvatarImageView
        android:id="@+id/avatarIv"
        android:layout_width="80dp"
        android:layout_height="80dp"
        android:layout_centerHorizontal="true"
        android:src="@drawable/avatar" />
```

##Advanced

对控件属性的设置，需要改变默认样式时，可选择修改以下属性
```JAVA
avatarImageView = (AvatarImageView) findViewById(R.id.avatarIv); 

//设置对话框的背景色
avatarImageView.setDialogBackgroundColor("#00AAAA"); 

//设置按钮点击后的颜色
avatarImageView.setBtnClickedColor("#00AAAA"); 

//设置dialog显示的动画
avatarImageView.setAnimResId(R.style.avatar_dialog_animation); 

//设置标题的颜色
avatarImageView.setTitleColor("#FFEEAA");  

//设置按钮的背景色
avatarImageView.setBtnBackgroundColor("#FFEEAA"); 

//设置标题下的分割线的颜色
avatarImageView.setTitleLineColor("#FFEEAA"); 

//设置按钮之间的分割线的颜色
avatarImageView.setLineColor("#FFEEAA"); 

//设置标题的padding
avatarImageView.setTitlePaddingTopBottom(30); 

//设置按钮的padding
avatarImageView.setBtnPaddingTopBottom(30); 

//设置标题的文字
avatarImageView.setTitleText("testTitle"); 

//设置拍照按钮的文字
avatarImageView.setPhotoButtonText("testPhotoText"); 

//设置选择照片的文字
avatarImageView.setChoosePicButtonText("testChooseText"); 

//设置dialog的角度
avatarImageView.setDialogCorner(20); 

//设置按钮文本的颜色
avatarImageView.setBtnTextColor("#FFEEAA"); 

//设置标题的文字大小
avatarImageView.setTitleTextSize(30); 

//设置按钮的文字大小
avatarImageView.setBtnTextSize(30); 

  ```
  
  
  头像设置成功的回调
  ```JAVA
  avatarImageView.setAfterCropListener(new AvatarImageView.AfterCropListener() {
            @Override
            public void afterCrop(Bitmap photo) {
                Toast.makeText(MainActivity.this,"设置新的头像成功",Toast.LENGTH_SHORT).show();
            }
        });
  ```
  
  需要设置拍照和图集页面关闭后的回调函数，来实现设置头像
  ```JAVA
  @Override
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        super.onActivityResult(requestCode, resultCode, data);

        //在拍照、选取照片、裁剪Activity结束后，调用的方法
        if(avatarImageView != null){
            avatarImageView.onActivityResult(requestCode,resultCode,data);
        }
    }
```
TIPS
Android 5.0 以上支持水波纹效果,Android 5.0之前是普通点击效果
