# Workshop-01


## AIM:

To Develop an android application to pass the data between the activities using Intent.

## EQUIPMENTS REQUIRED:

Latest Version Android Studio

## ALGORITHM:

Step 1:
Open Android Studio and create a new project with a Basic Activity.

Step 2:
In activity_main.xml, create a TextField (EditText) to input a Text and a Button labeled "Explicit Intent".

Step 3:
In MainActivity.java, get the Data from the TextField and set up an Explicit Intent to pass the Data to the second screen (SecondActivity).

Step 4:
Create SecondActivity.java and receive the Data passed from MainActivity using getIntent().

Step 5:
In SecondActivity,the received Data is displayed in a TextView.

Step 6:
Save and run the app. On clicking the "Explicit Intent" button, it will navigate to the second screen displaying the factorial.




## PROGRAM:
```
/*
Program to print the text “ExplicitIntent”.
Developed by: Sanjay.R
Registeration Number : 212222220038
*/
```
## Main Activity.java
```
package com.example.intentexample;

import android.content.Intent;
import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.EditText;
import androidx.appcompat.app.AppCompatActivity;

public class MainActivity extends AppCompatActivity {

    EditText name, age, email, contact;
    Button buttonSubmit;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        name = findViewById(R.id.editTextName);
        age = findViewById(R.id.editTextAge);
        email = findViewById(R.id.editTextEmail);
        contact = findViewById(R.id.editTextContact);
        buttonSubmit = findViewById(R.id.buttonSubmit);

        buttonSubmit.setOnClickListener(new View.OnClickListener() {
            @Override
            public void onClick(View view) {
                Intent intent = new Intent(MainActivity.this, DisplayActivity.class);
                intent.putExtra("name", name.getText().toString());
                intent.putExtra("age", age.getText().toString());
                intent.putExtra("email", email.getText().toString());
                intent.putExtra("contact", contact.getText().toString());
                startActivity(intent);
            }
        });
    }
}

```
## Display Activity.java
```
package com.example.intentexample;

import android.os.Bundle;
import android.widget.TextView;
import androidx.appcompat.app.AppCompatActivity;

public class DisplayActivity extends AppCompatActivity {

    TextView textViewName, textViewAge, textViewEmail, textViewContact;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_display);

        textViewName = findViewById(R.id.textViewName);
        textViewAge = findViewById(R.id.textViewAge);
        textViewEmail = findViewById(R.id.textViewEmail);
        textViewContact = findViewById(R.id.textViewContact);

        // Get data from intent
        String name = getIntent().getStringExtra("name");
        String age = getIntent().getStringExtra("age");
        String email = getIntent().getStringExtra("email");
        String contact = getIntent().getStringExtra("contact");

        // Set data to TextViews
        textViewName.setText("Name: " + name);
        textViewAge.setText("Age: " + age);
        textViewEmail.setText("Email: " + email);
        textViewContact.setText("Contact: " + contact);
    }
}


```
## Activity main.xml
```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:background="@drawable/bg4">

    <LinearLayout
        android:layout_width="370dp"
        android:layout_height="350dp"
        android:orientation="vertical"
        android:padding="24dp"
        android:layout_centerInParent="true"
        android:background="@drawable/blur"
        android:elevation="8dp">

        <EditText
            android:id="@+id/editTextName"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:backgroundTint="#6200EE"
            android:hint="Enter Name"
            android:minHeight="48dp"
            android:padding="10dp"
            android:textColor="#020202" />

        <EditText
            android:id="@+id/editTextAge"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:backgroundTint="#6200EE"
            android:hint="Enter Age"
            android:inputType="number"
            android:minHeight="48dp"
            android:padding="10dp"
            android:textColor="#000" />

        <EditText
            android:id="@+id/editTextEmail"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:backgroundTint="#6200EE"
            android:hint="Enter Email ID"
            android:inputType="textEmailAddress"
            android:minHeight="48dp"
            android:padding="10dp"
            android:textColor="#000" />

        <EditText
            android:id="@+id/editTextContact"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="10dp"
            android:backgroundTint="#6200EE"
            android:hint="Enter Contact Number"
            android:inputType="phone"
            android:minHeight="48dp"
            android:padding="10dp"
            android:textColor="#000" />

        <Button
            android:id="@+id/buttonSubmit"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:layout_marginTop="16dp"
            android:backgroundTint="#6200EE"
            android:text="Submit"
            android:textColor="#FFF" />
    </LinearLayout>
</RelativeLayout>

```
## Display activity.xml
```
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:background="@drawable/bg4"
    android:layout_width="match_parent"
    android:layout_height="match_parent">

    <LinearLayout
        android:layout_width="300dp"
        android:layout_height="300dp"
        android:orientation="vertical"
        android:padding="24dp"
        android:layout_centerInParent="true"
        android:background="@drawable/blur"
        android:elevation="8dp">

        <TextView
            android:id="@+id/textViewName"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Name:"
            android:textSize="18sp"
            android:textColor="#333333"
            android:layout_marginBottom="12dp" />

        <TextView
            android:id="@+id/textViewAge"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Age:"
            android:textSize="18sp"
            android:textColor="#333333"
            android:layout_marginBottom="12dp" />

        <TextView
            android:id="@+id/textViewEmail"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Email:"
            android:textSize="18sp"
            android:textColor="#333333"
            android:layout_marginBottom="12dp" />

        <TextView
            android:id="@+id/textViewContact"
            android:layout_width="match_parent"
            android:layout_height="wrap_content"
            android:text="Contact:"
            android:textSize="18sp"
            android:textColor="#333333" />
    </LinearLayout>
</RelativeLayout>


```
## OUTPUT


![WhatsApp Image 2025-05-16 at 17 44 23_35df40dc](https://github.com/user-attachments/assets/2fa053b5-a5f3-4ac8-964b-32495d5f3b73)
![WhatsApp Image 2025-05-16 at 17 44 23_054293ac](https://github.com/user-attachments/assets/c192b5be-18d4-4915-8a2b-cc6e20377abd)



## RESULT
Thus a Simple Android Application create a Explicit Intents using Android Studio is developed and executed successfully.
