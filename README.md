# Ex.No:2(b) To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## AIM:

To create a two screens , first screen will take one number input from user. After click on Factorial button, second screen will open and it should display factorial of the same number using Explicit Intents.


## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

1. Start the program.
2. Create two activities in Android Studio: `MainActivity` and `MainActivity2`.
3. Design the first screen with an `EditText` to enter a number and a **Factorial** button.
4. Initialize the input field and button in `MainActivity.java`.
5. Get the number entered by the user when the Factorial button is clicked.
6. Create an Explicit Intent to open `MainActivity2` and pass the number using `putExtra()`.
7. In `MainActivity2`, receive the number using `getIntent()` and `getIntExtra()`.
8. Calculate the factorial of the number using a loop.
9. Display the factorial result in a `TextView`.
10. Run the application and verify the output.
11. Stop the program.
    
## PROGRAM:
```
/*
Program to print the text “ExplicitIntent”.
Developed by: VISHWAJITH P
Registeration Number : 212225220122
*/
```
### MainActivity
```
package com.example.explicit;

import android.os.Bundle;

import androidx.appcompat.app.AppCompatActivity;
import android.view.View;
import android.content.Intent;
import android.widget.Button;
import android.widget.EditText;
import android.widget.Toast;

import com.example.explicit.R;

public class MainActivity extends AppCompatActivity {
    Button btn;
    EditText number;
    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
        btn=findViewById(R.id.btn);
        number=findViewById(R.id.editText1);
        btn.setOnClickListener(new View.OnClickListener(){
            public void onClick(View view){
                String input=number.getText().toString().trim();
                if(input.isEmpty()){
                    Toast.makeText(MainActivity.this,"Please enter a number",
                            Toast.LENGTH_SHORT).show();
                    return;
                }
                int n;
                try{
                    n=Integer.parseInt(input);
                }
                catch(NumberFormatException e){
                    Toast.makeText(MainActivity.this,"Please Enter a Valid Number",
                            Toast.LENGTH_SHORT).show();
                    return;
                }
                if(n<0||n>20)
                {
                    Toast.makeText(MainActivity.this,"Enter a number between 0 and 20",
                            Toast.LENGTH_SHORT).show();
                    return;
                }
                Intent i=new Intent(MainActivity.this, MainActivity2.class);
                i.putExtra("number",n);
                startActivity(i);
            }
        });
    }
}
```
### MainActivity2
```
package com.example.explicit;

import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.widget.TextView;
import android.content.Intent;

public class MainActivity2 extends AppCompatActivity{

    TextView result;
    @Override
    protected void onCreate(Bundle savedInstanceState){
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main2);
        result=findViewById(R.id.result1);
        Intent intent=getIntent();
        int n=intent.getIntExtra("number",0);
        long factorial=1;
        for(int i=1;i<=n;i++){
            factorial=factorial*i;
        }
        result.setText("Factorial of "+n+" = "+factorial);
    }
}
```
### activity_main
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:id="@+id/main"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#D303FFFB"
    tools:context=".MainActivity">

    <TextView
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:fontFamily="serif"
        android:text="@string/exp_title"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@+id/textView"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.496"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.573" />

    <TextView
        android:id="@+id/textView"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="156dp"
        android:fontFamily="serif"
        android:text="@string/enter_number_instruction"
        android:textSize="20sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toTopOf="@+id/btn"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.493"
        app:layout_constraintStart_toStartOf="parent" />

    <Button
        android:id="@+id/btn"
        style="@style/Widget.AppCompat.Button"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginBottom="328dp"
        android:background="#1CC33B"
        android:backgroundTint="#FF1A1A"
        android:backgroundTintMode="add"
        android:shadowColor="#621414"
        android:text="@string/calculate_factorial"
        android:textAppearance="@style/TextAppearance.AppCompat.Medium"
        android:textColor="#FFEB3B"
        android:textColorHighlight="#BA1E1E"
        android:textColorHint="#5D0404"
        android:textColorLink="#20CE08"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:strokeColor="#B41212" />

    <EditText
        android:id="@+id/editText1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="52dp"
        android:autofillHints=""
        android:ems="10"
        android:hint="@string/number_hint"
        android:inputType="text"
        android:textColorHighlight="#000000"
        android:textSize="18sp"
        app:layout_constraintBottom_toTopOf="@+id/btn"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView"
        app:layout_constraintVertical_bias="0.31" />

</androidx.constraintlayout.widget.ConstraintLayout>

```
### activity_main2
```
<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="#35A5D9">

    <TextView
        android:id="@+id/textView2"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="112dp"
        android:fontFamily="serif"
        android:text="Exp 2b Explicit Intent"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.496"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent" />

    <TextView
        android:id="@+id/textView3"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginTop="68dp"
        android:fontFamily="serif"
        android:text="Factorial of the Number appears here"
        android:textSize="20sp"
        android:textStyle="bold"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintHorizontal_bias="0.497"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView2" />

    <TextView
        android:id="@+id/result1"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:fontFamily="serif"
        android:text="Result"
        android:textSize="24sp"
        android:textStyle="bold"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toBottomOf="@+id/textView3"
        app:layout_constraintVertical_bias="0.174" />

</androidx.constraintlayout.widget.ConstraintLayout>

```

## OUTPUT

<img width="1920" height="1080" alt="Screenshot 2026-11-03 110817" src="https://github.com/user-attachments/assets/7cd79ada-4f39-4122-89f0-1c4d69f0fbf5" />

<img width="1920" height="1080" alt="Screenshot 2026-11-03 110829" src="https://github.com/user-attachments/assets/f73dad7e-b39d-47d0-ad99-fae4c837ccb8" />


## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.


