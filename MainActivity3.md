# TUGAS-Selection-Widget
Biodata dengan Auto Complete text
MainActivity3.main
package com.example.biodata;

import androidx.appcompat.app.AppCompatActivity;

import android.os.Bundle;
import android.provider.MediaStore;
import android.view.View;
import android.widget.ArrayAdapter;
import android.widget.AutoCompleteTextView;
import android.widget.Button;
import android.widget.CheckBox;
import android.widget.EditText;
import android.widget.RadioButton;
import android.widget.Toast;

public class MainActivity3 extends AppCompatActivity implements View.OnClickListener {

    EditText YName;
    RadioButton rbMan,rbWoman;
    Button btShow,btClear;
    AutoCompleteTextView Activ;
    CheckBox cb1,cb2,cb3,cb4,cb5,cb6;

    private static final String[] CITIES = new String[] {
            "Jember", "Malang", "Pasuruan", "Probolinggo", "Bondowoso", "Situbondo", "Surabaya", "Madiun", "Blitar"
    };

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main3);

        AutoCompleteTextView editText = findViewById(R.id.actv);
        ArrayAdapter<String> adapter = new ArrayAdapter<String>(this,android.R.layout.simple_list_item_1, CITIES);
        editText.setAdapter(adapter);

        YName = (EditText) findViewById(R.id.nName);
        rbMan = (RadioButton) findViewById(R.id.radioButton3);
        rbWoman = (RadioButton) findViewById(R.id.radioButton4);
        Activ = (AutoCompleteTextView) findViewById(R.id.actv);
        cb1 = (CheckBox) findViewById(R.id.K1L);
        cb2 = (CheckBox) findViewById(R.id.K1R);
        cb3 = (CheckBox) findViewById(R.id.K2L);
        cb4 = (CheckBox) findViewById(R.id.K2R);
        cb5 = (CheckBox) findViewById(R.id.K3L);
        cb6 = (CheckBox) findViewById(R.id.K3R);

        btShow = (Button) findViewById(R.id.buttonshow);

        btShow.setOnClickListener(this);
    }

    @Override
    public void onClick(View view) {
        String vNama = YName.getText().toString();
        String a = "";
        String City = Activ.getText().toString();
        String Lg = "";

        //Percabangan Radio Button
        if(rbMan.isChecked()){
            a+="Man";
        }
        if(rbWoman.isChecked()){
            a+="Woman";
        }

        //Percabangan Radio Button
        if(cb1.isChecked()){
            Lg+="Indonesia";
        }
        if(cb2.isChecked()) {
            Lg +="English";
        }
        if(cb3.isChecked()){
            Lg+="Japanese";
        }
        if(cb4.isChecked()) {
            Lg += "France";
        }
        if(cb5.isChecked()){
            Lg+="Java";
        }
        if(cb6.isChecked()) {
            Lg += "Spain";
        }
        Toast.makeText(this, "Name : "+vNama+ "\n" + "Gender : "+a+ "\n" + "City : "+City+"\n" + "Language : "+Lg, Toast.LENGTH_SHORT).show();
    }
}
