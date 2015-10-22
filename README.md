# 2015-10-22
//安卓页面跳转。
package com.example.test1;

import android.os.Bundle;
import android.app.Activity;
import android.content.Intent;
import android.view.Menu;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

public class MainActivity extends Activity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);   //此处必须和当前页面保持一直
        
       Button btn1 = (Button)findViewById(R.id.button1);//登录按钮链接
       btn1.setOnClickListener(new OnClickListener() {   //OnClickListener 是一种处理的是点击事件的接口。
		
		@Override
		public void onClick(View arg0) {
			// TODO Auto-generated method stub
			
			EditText edt1 = (EditText)findViewById(R.id.editText1);
			EditText edt2 = (EditText)findViewById(R.id.editText2);
			String userName = edt1.getText().toString();
			String passWord = edt2.getText().toString();
			
			if(userName.equals("admin") && passWord.equals("123")){  //帐号密码固定
				Toast.makeText(MainActivity.this,"登录成功",Toast.LENGTH_SHORT).show();
				
				Intent i = new Intent();
				i.setClass(MainActivity.this, HomeActivity.class );
				startActivity(i);  // 等于startActivity(new Intent(A.this,B.class));
				
			}
			else{
				Toast.makeText(MainActivity.this,"登录失败",Toast.LENGTH_SHORT).show();
			}
		}
	});
       
    }


    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        // Inflate the menu; this adds items to the action bar if it is present.
        getMenuInflater().inflate(R.menu.main, menu);
        return true;
    }
    
}
