# Index

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

## Java
En la carpeta java estara todo nuestro codigo

## Res
Estaran los recursos, por ejemplo pantallas

### drawable
Imagenes y contenido multimedia

# Proyecto

### Activity
Por cada actividad tenemos un archivo kotlin y el archivo xml que contiene el diseño de la aplicacion.

### View
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
# Layout

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