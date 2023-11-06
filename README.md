package com.example.fibonanccisequence;

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.TextView;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

public class  MainActivity extends AppCompatActivity {
    private int count = 1;
    private TextView showcount;
    private Button mbtnToast,mbtnCount, mbtnRestart;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        showcount = findViewById(R.id.show_count);
        mbtnToast = findViewById(R.id.btnToast);
        mbtnCount = findViewById(R.id.btnCount);
        mbtnRestart = findViewById(R.id.btnRestart);

        mbtnToast.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                showToast();
            }
        });

        mbtnCount.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {

                countTop();
            }
        });
        mbtnRestart.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {

                count = 1;
                showcount.setText("1");
            }
        });
    }

    public void showToast() {
        Toast toast = Toast.makeText(this, "Hello Toast!", Toast.LENGTH_SHORT);
        toast.show();
    }
    public void countTop() {
        if (count < 0) {
            count = 0;
        }
        int result = generateFibonacci(count);
        showcount.setText(Integer.toString(result));
        count++;
    }

    private int generateFibonacci(int n) {
        if (n <= 0) {
            return 0;
        }
        else if (n == 1) {
            return 1;
        }

        int first = 1;
        int second = 1;

        for (int i = 2; i <= n; i++) {
            int next = first + second;
            first = second;
            second = next;
        }

        return second;
    }
}
