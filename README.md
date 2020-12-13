# MarqueeView  [ ![MarqueeView](https://api.bintray.com/packages/sfsheng0322/maven/MarqueeView/images/download.svg) ](https://bintray.com/sfsheng0322/maven/MarqueeView/_latestVersion)

俗名：可垂直跑、可水平跑的跑马灯  
学名：可垂直翻、可水平翻的翻页公告

### 效果图

<img src="/resources/MarqueeView.gif" style="width: 30%;">

#### Gradle:

    compile 'com.sunfusheng:MarqueeView:<latest-version>'

#### 属性

| Attribute 属性          | Description 描述 | 
|:---				     |:---| 
| mvAnimDuration         | 一行文字动画执行时间 | 
| mvInterval         | 两行文字翻页时间间隔 | 
| mvTextSize         | 文字大小 | 
| mvTextColor         | 文字颜色 | 
| mvGravity         | 文字位置:left、center、right | 
| mvSingleLine         | 单行设置 |
| mvDirection        | 动画滚动方向:bottom_to_top、top_to_bottom、right_to_left、left_to_right |
| mvFont             | 设置字体 |

#### XML

    <com.sunfusheng.marqueeview.MarqueeView
        android:id="@+id/marqueeView"
        android:layout_width="match_parent"
        android:layout_height="30dp"
        app:mvAnimDuration="1000"
        app:mvDirection="bottom_to_top"
        app:mvInterval="3000"
        app:mvTextColor="@color/white"
        app:mvTextSize="14sp"
        app:mvSingleLine="true"
        app:mvFont="@font/huawenxinwei"/>

#### 设置字符串列表数据，或者设置自定义的Model数据类型

    MarqueeView marqueeView = (MarqueeView) findViewById(R.id.marqueeView);

    List<String> messages = new ArrayList<>();
    messages.add("1. 大家好，我是孙福生。");
    messages.add("2. 欢迎大家关注我哦！");
    messages.add("3. GitHub帐号：sunfusheng");
    messages.add("4. 新浪微博：孙福生微博");
    messages.add("5. 个人博客：sunfusheng.com");
    messages.add("6. 微信公众号：孙福生");
    marqueeView.startWithList(messages);

    // 或者设置自定义的Model数据类型
    public class CustomModel implements IMarqueeItem {
        @Override
        public CharSequence marqueeMessage() {
            return "...";
        }
    }

    List<CustomModel> messages = new ArrayList<>();
    marqueeView.startWithList(messages);
    
    // 在代码里设置自己的动画
    marqueeView.startWithList(messages, R.anim.anim_bottom_in, R.anim.anim_top_out);

#### 设置字符串数据

    String message = "心中有阳光，脚底有力量！心中有阳光，脚底有力量！心中有阳光，脚底有力量！";
    marqueeView.startWithText(message);
    
    // 在代码里设置自己的动画
    marqueeView.startWithText(message, R.anim.anim_bottom_in, R.anim.anim_top_out);

#### 设置事件监听

    marqueeView.setOnItemClickListener(new MarqueeView.OnItemClickListener() {
        @Override
        public void onItemClick(int position, TextView textView) {
            Toast.makeText(getApplicationContext(), String.valueOf(marqueeView1.getPosition()) + ". " + textView.getText(), Toast.LENGTH_SHORT).show();
        }
    });

#### 重影问题可参考以下解决方案

在 Activity 或 Fragment 中

    @Override
    public void onStart() {
        super.onStart();
        marqueeView.startFlipping();
    }

    @Override
    public void onStop() {
        super.onStop();
        marqueeView.stopFlipping();
    }

在 ListView 或 RecyclerView 的 Adapter 中

    @Override
    public void onViewDetachedFromWindow(@NonNull ViewHolder holder) {
        super.onViewDetachedFromWindow(holder);
        holder.marqueeView.stopFlipping();
    }

<br/>

### 扫一扫[Fir.im](https://fir.im/MarqueeView)二维码下载APK

<img src="/resources/fir.im.png">

<br/>

### 个人微信公众号

<img src="http://ourvm0t8d.bkt.clouddn.com/wx_gongzhonghao.png">

<br/>

### 打点赏给作者加点油^_^

<img src="http://ourvm0t8d.bkt.clouddn.com/wx_shoukuanma.png" >

<br/>

### 关于我

[GitHub: sunfusheng](https://github.com/sunfusheng)  

[个人邮箱: sfsheng0322@126.com](https://mail.126.com/)
  
[个人博客: sunfusheng.com](http://sunfusheng.com/)
  
[简书主页](http://www.jianshu.com/users/88509e7e2ed1/latest_articles)
  
[新浪微博](http://weibo.com/u/3852192525) 