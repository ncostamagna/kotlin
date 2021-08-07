# Index
- [Instalacion](#instalacion)
    + [Configuracion dispositivo](#configuracion-dispositivo)
- [Estructura](#estructura)
  * [Manifest](#manifest)
  * [Java](#java)
  * [Res](#res)
    + [drawable](#drawable)
    + [mipmap](#mipmap)
    + [values](#values)
      - [string](#string)
- [Proyecto](#proyecto)
  * [Activity](#activity)
  * [View](#view)
    + [Data Binding](#data-binding)
- [Layout](#layout)
    + [Lineal](#lineal)
- [Logs](#logs)
  * [Logcat](#logcat)
  * [Log](#log)
- [Mensajes](#mensajes)
  * [Toasts](#toasts)

<small><i><a href='http://ecotrust-canada.github.io/markdown-toc/'>Table of contents generated with markdown-toc</a></i></small>

# Instalacion
https://developer.android.com/studio/install?hl=es-419

### Configuracion dispositivo
Primero tenemos que indicarnos como programador de la siguiente manera<br />
*sistema > acerca dispositivo > numero de compilacion*<br />
<br />
Luego configurarlo de la siguiente manera:<br />
*sistema > avanzado > Opciones programador*

- vemos que este activo
- que diga permanecer activo
- Depuracion por USB

# Estructura

## Manifest
Podemos configurar ciertas cosas
```xml
<application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher" // Icono de la aplicacion
        android:label="@string/app_name" // Nombre de la aplicacion
        android:roundIcon="@mipmap/ic_launcher_round" // Icono redondo
        android:supportsRtl="true"
        android:theme="@style/AppTheme">

        // Aca vamos a tener todas las actividades
        <activity android:name=".MainActivity">
            <intent-filter>
                // Main activiti va a ser la principal
                <action android:name="android.intent.action.MAIN" /> 

                // La primera que se va a lanzar
                <category android:name="android.intent.category.LAUNCHER" />
            </intent-filter>
        </activity>
    </application>
```

## Java
En la carpeta java estara todo nuestro codigo

## Res
Estaran los recursos, por ejemplo pantallas

### drawable
Imagenes y contenido multimedia

### mipmap
POdemos agregar iconos. Tenemos varias resoluciones y uno para cuadrado y otro para redondo.<br />
Damos click der en mipmap > New > Image asset<br />
Seleccionamos la imagen que nosotros queramos

### values
Para generar valores de diferentes idiomas generamos una carpeta **values-es** por ejemplo (para español)

#### string
Vamos a poner todos los textos estaticos de nuestra aplicacion<br />
Con **Alt + Enter** los generamos de una forma facil

```xml
// translatable -> No tiene traduccion
<resources>
    <string name="app_name" translatable="false">Mi edad canina</string>
    <string name="your_age">Your age</string>
</resource>
```

```kotlin
val result = getString(R.string.lalita)
```

# Proyecto

## Activity
Por cada actividad tenemos un archivo kotlin y el archivo xml que contiene el diseño de la aplicacion.

## View
Todas las cosas que podamos ver en la pantalla son View. Como por ejemplo imagenes, texto, botones, etc..<br />
Tenemos atributos como color, tamaño, etc..
```xml
<ImageView
    android:layout_width="match_parent"   // Todo lo que abarca el padre
    android:layout_height="wrap_content"
    android:src="@drawable/dog_meme"
    android:adjustViewBounds="true"  // Quitamos espacios en blanco
    android:text="Hello World!" />

<TextView
    android:layout_width="match_parent"  // Todo lo que abarca el padre
    android:layout_height="wrap_content"
    android:padding="16dp"
    android:textColor="@android:color/black"
    android:textSize="18sp"
    android:text="@string/instructions" />

<EditText
    android:id="@+id/age_edit" // con los IDS vamos a poder usar esto en el codigo
    android:layout_width="match_parent"  // Todo lo que abarca el padre
    android:layout_height="wrap_content" // Solo lo que contiene
    android:layout_marginStart="16dp"
    android:layout_marginEnd="16dp"
    android:inputType="number" // el tipo de dato que recibe
    android:gravity="center" // alinear el texto
    android:hint="@string/your_age" // texto q se muestra como ayuda
    tools:text="La puta madre" // Solo lo vamos a ver en el preview, no en la app
/>
```

```kotlin
val ageEdit = findViewById<EditText>(R.id.age_edit)

val resultText = findViewById<TextView>(R.id.result_text)
resultText.text = "Lala"

val button = findViewById<Button>(R.id.button)
button.setOnClickListener {
    // cuando demos click al boton se ejecutara esto
}
```

### Data Binding
Utilizar **findViewById** no es permormante porque es pesado, lo mejor es utilizar **binding**<br /><br />

Vamos a **build.gradle** y despues damos click en **sync**
```groovy
apply plugin: 'kotlin-kapt'

android {
    ...
    dataBinding {
        enabled = true
    }

    // O podriamos usar tambien 
    buildFeatures {
        dataBinding true
    }
}
```
En el layout damos click en **Convert to data binding layout<br />
```xml
<layout>
    <data>

    </data>

    // todo mi layout (LiearLayout)
</layout>
```
```kotlin
val binding = ActivityMainBinding.inflate(layoutInflater)
setContentView(binding.root)

val ageEdit = binding.ageEdit
```


# Layout
Para elegir lo mejor es elegir la opcion en la cual tengas menos Views Layout<br />
<img src="" />

### Lineal
Los pone uno al lado del otro, de manera vertical u horizontal

```xml
<LinearLayout
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:orientation="vertical"
    tools:context=".MainActivity">

...

</LinearLayout>
```

### Frame
Diseñado para mostrar un view a la vez, imagen, video, boton, ect..<br />
Solo una a la vez, los view se traslapan entre ellos cuando se generan

### Relative
Acomodamos los View de la manera que queramos, en la parte de abajo, en el centro, etc..

### Contraint
Todo se hace en la parte del diseño, muy versatil pero se usa para pocos Views<br />


# Logs

## Logcat
Para ver los errores lo podemos ver en la pestaña de abajo de **Logcat** seleccionando **error**

## Log
Podemos hacer logs nuestros, podemos definirle el nivel de log

```kotlin
// recibe un tag y un mensaje
Log.d("MainActivity", "Mi actividad")
```
Existen 5 niveles diferentes:
- verbose: imprimir cualquier cosa
- debug: imprimir cualquier cosa 
- info: algo se pone un poco peligroso
- warm: algo se pone mas peligroso
- error: ya puede ocurrir un error grave
- assert: 

```kotlin
Log.v("MainActivity", "Mi verbose")
Log.d("MainActivity", "Mi debug")
Log.i("MainActivity", "Mi info")
Log.w("MainActivity", "Mi warm")
Log.e("MainActivity", "Mi error")
```

# Mensajes

## Toasts
Mensaje que aparene en la parte inferior de la pantalla, aparece y se va
```kotlin
// contexto -> de donde se esta llamando
// y duracion
Toast.makeText(this, "Mi mensaje", Toast.LENGTH_SHORT).show()
```