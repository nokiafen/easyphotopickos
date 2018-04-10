# easyphotopickos

* 一款图片选择编辑工具，仿ios风格，实现快速选择图片（拍照/相册）,裁剪功能

 * gif预览 图片有点大，点开查看吧！
 
![image](https://github.com/nokiafen/easyphotopickos/tree/master/preview/movie.gif)

使用：修改你的project 和module 的gradle如下
```gradle

//root project

allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}
    
//module project

    	dependencies {
	        compile 'com.github.nokiafen:easyphotopickos:1.0.0'
	}
  
```
# 代码实现：

 1：打开
 
```java

   startActivityForResult(new Intent(this, ImagePickActivity.class), ImagePickActivity.PICK_REQUESTCODE);  //打开操作
  
```

 2：接收返回图片

```java

    @Override
    protected void onActivityResult(int requestCode, int resultCode, Intent data) {
        if (requestCode == ImagePickActivity.PICK_REQUESTCODE && resultCode == Activity.RESULT_OK) {
            String path = (String) data.getExtras().get(ImagePickActivity.PATH);  //你要的图片在此
            Bitmap bmp = UploadUtil.getTargetBitmap(path, 800, 800);
            ((ImageView) findViewById(R.id.iv_img)).setImageBitmap(bmp);
        }
        super.onActivityResult(requestCode, resultCode, data);
    }

```
 
    
