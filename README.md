# Calculadora-de-Formulas-
Aplicación básica para calcular la Formula General y la Pendiente.
package com.rick.calcuformulas;
import androidx.appcompat.app.AppCompatActivity;
import android.os.Bundle;
import android.view.View;
import android.widget.EditText;
import android.widget.TextView;
public class MainActivity extends AppCompatActivity {

    private EditText n1, n2, n3, x1, x2, y1, y2;//DECLARAMOS LAS VARIABLES A UTILIZAR PARA PEDIR DATOS
    private TextView resx1, resx2, rm;//DECLARAMOS LAS VARIABLES A UTILIZAR PARA DEVOLVER RESULTADOS

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
//INSTANCIAMOS TODAS Y CADA UNA DE LAS VARIABLES DECLARADAS ARRIBA
        n1 = findViewById(R.id.n1);
        n2 = findViewById(R.id.n2);
        n3 = findViewById(R.id.n3);
        resx1 = findViewById(R.id.resx1);
        resx2 = findViewById(R.id.resx2);
        x1=findViewById(R.id.x1);
        x2 =findViewById(R.id.x2);
        y1=findViewById(R.id.y1);
        y2=findViewById(R.id.y2);
        rm= findViewById(R.id.rm);

    }
//AGREGAMOS UN METODO LIMPIAR PARA LOS VALORES DESPUES DE REALIZAR UNA OPERAACION
    public void limpiar() {
        resx1.setText("");
        resx2.setText("");

    }
    public void calcula(View view) {//MANDAMOS A LLAMAR AL METODO CREADO EN ESTE CASO CALCULA PARA LA FG
        String valorA = n1.getText().toString();//GUARDA LOS DATOS RECIBIDOS COMO CADEMAS DE CARACTERES
        String valorB = n2.getText().toString();
        String valorC = n3.getText().toString();
        double numa = Integer.parseInt(valorA);//DEVUELVE DATOS EN ENTERO CONVIRTIENDO DE STRING A ENTERO
        double numb = Integer.parseInt(valorB);
        double numc = Integer.parseInt(valorC);
        double r = (numb * numb) - (4 * numa * numc);//REALIZA LA OPERACION DE LA FORMULA DE B*B-4A*C
        double raiz = Math.sqrt(r);//REALIZA LA RAIZ DE LA OPERACION DE LA R
        limpiar();
        if (r > 0) {//VALIDA SI EL RESULTADO ES VALIDO Y RESUELVE LA ECUACION.
            double x1 = (-numb + raiz) / 2 * numa;
            String rx1 = String.valueOf(x1);
            resx1.setText(rx1);
            double x2 = (-numb - raiz) / 2 * numa;
            String rx2 = String.valueOf(x2);
            resx2.setText(rx2);
        } else if (r == 0) {//VALIDA SI EL RESULTADO ES IGUAL A CERO PARA PODER RESLOVER LA ECUACION
            double x0 = -(numb) / (2 * numa);
            String rx0 = String.valueOf(x0);
            resx1.setText(rx0);
            resx2.setText("");
        } else {//SI EL RESLUTADO ES DIFERENTE NO TIENE SOLUCION LA ECUACION
            resx1.setText("");
            resx2.setText("");
        }
    }
    public void calcula2(View view) {//MANDAMOS A LLAMAR AL METODO CREADO EN ESTE CASO CALCULA2 PARA LA FP
        String valorx1 = x1.getText().toString();//GUARDA LOS DATOS RECIBIDOS COMO CADEMAS DE CARACTERES
        String valorx2 = x2.getText().toString();
        String valory1 = y1.getText().toString();
        String valory2 = y2.getText().toString();
        int numx1 = Integer.parseInt(valorx1);//DEVUELVE DATOS EN ENTERO CONVIRTIENDO DE STRING A ENTERO
        int numx2 = Integer.parseInt(valorx2);
        int numy1 = Integer.parseInt(valory1);
        int numy2 = Integer.parseInt(valory2);

        double x = numx2 - numx1;//REALIZA LA OPERACION DE X2-X1
        double y = numy2 - numy1;//REALIZA LA OPERACION DE Y2-Y1
        double m = y / x;//REALIZA LA OPERACION DE LA FORMULA DE LA PENDIENTE
        String p = String.valueOf(m);
        rm.setText( p);//REGRESA EL RESULTADO DE LA OPERACION EN UN TEXTVIEW
    }
    }

