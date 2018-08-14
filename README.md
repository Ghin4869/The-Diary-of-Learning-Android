# The-Diary-of-Learning-Android
The journey of learning android
## 第一次学习
1.代码
### FirstActivity
package com.example.activitytest;

import android.content.Intent;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.util.Log;
import android.view.Menu;
import android.view.MenuItem;
import android.view.View;
import android.widget.Button;
import android.widget.Toast;

import activitytest.example.com.activitytest.R;

public class FirstActivity extends AppCompatActivity {

    @Override
    public boolean onOptionsItemSelected(MenuItem item) {
        switch (item.getItemId()){
            case R.id.add_item:
                Toast.makeText(this, "You clicked Add", Toast.LENGTH_SHORT).show();
                break;
            case R.id.remove_item:
                Toast.makeText(this, "You clicked Remove", Toast.LENGTH_SHORT).show();
                break;
            default:
        }
        return true;
        //        return super.onOptionsItemSelected(item);
    }

    @Override
    public boolean onCreateOptionsMenu(Menu menu) {
        getMenuInflater().inflate(R.menu.main, menu);
        return true;
//        return super.onCreateOptionsMenu(menu);
    }

    @Override
    protected void onCreate(Bundle savedInstanceState) {

        super.onCreate(savedInstanceState);
        Log.d("FirstActivity", this.toString());                 //standard启动模式，在FirstActivity的基础上启动FirstActivity
        setContentView(R.layout.first_layout);
        Button button1 = (Button)findViewById(R.id.button_1);
        button1.setOnClickListener(new View.OnClickListener(){
            @Override
            public void onClick(View v){
//                Toast.makeText(FirstActivity.this, "You clicked Button 1", Toast.LENGTH_SHORT).show();   第一次修改
//                Intent intent=new Intent(FirstActivity.this, SecondActivity.class);     //显式Intent
//                startActivity(intent);
//                  Intent intent=new Intent("com.example.activitytest.ACTION_START");   //隐式Intent
//                  startActivity(intent);
//                  String data="Hello SecondActivity";               //第二次修改
//                  Intent intent=new Intent(FirstActivity.this, SecondActivity.class);
//                  intent.putExtra("extra_data", data);
//                  startActivity(intent);
                Intent intent=new Intent(FirstActivity.this, FirstActivity.class);
                startActivity(intent);
        }
        });
    }
}
### SecondActivity
package com.example.activitytest;

import android.content.Intent;
import android.support.v7.app.AppCompatActivity;
import android.os.Bundle;
import android.util.Log;

import activitytest.example.com.activitytest.R;

public class SecondActivity extends AppCompatActivity {

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.second_layout);
        Intent intent=getIntent();
        String data=intent.getStringExtra("extra_data");
        Log.d("SecondActivity", data);

    }
}
