# sumofgiven3numbers
xml file-
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp"
    tools:context=".MainActivity">

    <EditText
        android:id="@+id/number1EditText"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Enter number 1" />

    <EditText
        android:id="@+id/number2EditText"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/number1EditText"
        android:layout_marginTop="16dp"
        android:hint="Enter number 2" />

    <EditText
        android:id="@+id/number3EditText"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/number2EditText"
        android:layout_marginTop="16dp"
        android:hint="Enter number 3" />

    <Button
        android:id="@+id/calculateButton"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/number3EditText"
        android:layout_marginTop="16dp"
        android:text="Calculate" />

    <TextView
        android:id="@+id/resultTextView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_below="@id/calculateButton"
        android:layout_marginTop="16dp"
        android:textSize="18sp"
        android:text="The sum of the three numbers will be displayed here." />

</RelativeLayout>

java file-
package com.example.sumofgiven3numbers;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import android.widget.TextView;

public class MainActivity extends AppCompatActivity {

    private EditText number1EditText;
    private EditText number2EditText;
    private EditText number3EditText;
    private Button calculateButton;
    private TextView resultTextView;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        number1EditText = findViewById(R.id.number1EditText);
        number2EditText = findViewById(R.id.number2EditText);
        number3EditText = findViewById(R.id.number3EditText);
        calculateButton = findViewById(R.id.calculateButton);
        resultTextView = findViewById(R.id.resultTextView);

        calculateButton.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View v) {
                String number1String = number1EditText.getText().toString();
                String number2String = number2EditText.getText().toString();
                String number3String = number3EditText.getText().toString();

                if (number1String.isEmpty() || number2String.isEmpty() || number3String.isEmpty()) {
                    resultTextView.setText("Please enter all three numbers.");
                    return;
                }

                double number1 = Double.parseDouble(number1String);
                double number2 = Double.parseDouble(number2String);
                double number3 = Double.parseDouble(number3String);
                double sum = number1 + number2 + number3;

                resultTextView.setText("The sum of the three numbers is: " + sum);
            }
        });
    }
}
