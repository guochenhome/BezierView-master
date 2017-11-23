# BezierView
练习贝塞尔曲线的小例子,具体详情请见博客:

[Android开发-贝塞尔曲线初体验]

[Android开发之贝塞尔曲线进阶篇（仿直播送礼物，饿了么购物车动画）]
```
	allprojects {
		repositories {
			...
			maven { url 'https://jitpack.io' }
		}
	}

	dependencies {
	        compile 'com.github.guochenhome:BezierView-master:1.4.1'
	}

```
-------
购物车效果
```
public class ShoppingCartActivity extends AppCompatActivity {

    private ImageView iv_shop_add;
    private ImageView iv_shop_cart;
    private ViewGroup mViewGroup;

    private int mShoppingCartWidth;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_shoppingcart);
        initView();
        getData();

        ViewTreeObserver viewTreeObserver = iv_shop_cart.getViewTreeObserver();
        viewTreeObserver.addOnGlobalLayoutListener(new ViewTreeObserver.OnGlobalLayoutListener() {
            @Override
            public void onGlobalLayout() {
                iv_shop_cart.getViewTreeObserver().removeOnGlobalLayoutListener(this);
                mShoppingCartWidth = iv_shop_cart.getMeasuredWidth();
            }
        });

    }

    private void getData() {
        iv_shop_add.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                //获取商品坐标
                int[] goodsPoint = new int[2];
                iv_shop_add.getLocationInWindow(goodsPoint);

                //获取购物车坐标
                int[] shoppingCartPoint = new int[2];
                iv_shop_cart.getLocationInWindow(shoppingCartPoint);


                //生成商品View
                GoodsView goodsView = new GoodsView(ShoppingCartActivity.this);
                goodsView.setCircleStartPoint(goodsPoint[0], goodsPoint[1]);
                goodsView.setCircleEndPoint(shoppingCartPoint[0] + mShoppingCartWidth / 2, shoppingCartPoint[1]);
                //添加View并执行动画
                mViewGroup.addView(goodsView);
                goodsView.startAnimation();

            }
        });

    }

    private void initView() {
        iv_shop_add = (ImageView) findViewById(R.id.iv_shop_add);
        iv_shop_cart = (ImageView) findViewById(R.id.iv_shop_cart);
        mViewGroup = (ViewGroup) getWindow().getDecorView();

    }
```