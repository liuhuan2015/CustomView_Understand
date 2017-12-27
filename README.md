# CustomView_Understand
android中自定义属性的理解
自定义属性的步骤:<br>
>一,自定义一个CustomView(extends View)类<br>
>二,编写values/attrs.xml,在其中编写attr,declare-styleable,item等标签元素<br>
>三,在布局文件中使用自定义属性(这里要注意namespace问题,如果declare-styleable的name值为自定义的类名,相对来说会省事一些)<br>
>四,在CustomView的构造方法中中通过TypedArray获取自定义的属性<br>

TypedArray的作用?<br>
一般我们会使用TypedArray来获取布局文件中的自定义属性的值,其实通过构造方法中的AttributeSet参数我们也是可以获取到自定义属性的值的,但是当自定义属性的值是
引用类型(如:@dimen/dp100)时,使用AttributeSet参数获取到的值会是@+数字的字符串,而TypedArray则可以帮助我们获取到我们真正想要的数值.<br>
博文中是这样写的:
>TypedArray其实是用来简化我们的工作的，比如上例，如果布局中的属性的值是引用类型（比如：@dimen/dp100），如果使用AttributeSet去获得最终的像素值，<br>
>那么需要第一步拿到id，第二步再去解析id。而TypedArray正是帮我们简化了这个过程。

declare-styleable的作用?<br>
博文中是这样写的:
>styleale的出现系统可以为我们完成很多常量（int[]数组，下标常量）等的编写，简化我们的开发工作（想想如果一堆属性，自己编写常量，你得写成什么样的代码）。
>那么大家肯定还知道declare-styleable的name属性，一般情况下写的都是我们自定义View的类名。主要为了直观的表达，该declare-styleable的属性，
>都是该View所用的。

总结:
>attrs.xml里面的declare-styleable以及item，android会根据其在R.java中生成一些常量方便我们使用(aapt干的)，本质上，
我们可以不声明declare-styleable仅仅声明所需的属性即可。
>我们在View的构造方法中，可以通过AttributeSet去获得自定义属性的值，但是比较麻烦，而TypedArray可以很方便的便于我们去获取。
>我们在自定义View的时候，可以使用系统已经定义的属性。




