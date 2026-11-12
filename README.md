import 'package:flutter/material.dart'; // Importa las herramientas de Flutter para crear interfaces gráficas.

// Esta función es el punto de inicio de la aplicación.
void main() { // Define la función principal del programa.
  runApp(const MyApp()); // Ejecuta la aplicación y muestra el widget principal.
} // Finaliza la función main.

// Esta clase representa la aplicación principal.
class MyApp extends StatelessWidget { // Crea un widget sin estado que no necesita modificar sus datos internos.
  const MyApp({super.key}); // Define el constructor de la clase y recibe una clave opcional.

  @override // Indica que se sobrescribe el método build de StatelessWidget.
  Widget build(BuildContext context) { // Construye la estructura visual de la aplicación.
    return MaterialApp( // Configura la aplicación utilizando el diseño Material de Flutter.
      title: 'SALUDO UAE', // Establece el título de la aplicación.
      theme: ThemeData( // Define el tema visual general de la aplicación.
        colorScheme: ColorScheme.fromSeed(seedColor: Colors.blue), // Crea una combinación de colores basada en el color azul.
      ), // Finaliza la configuración del tema.
      home: const MyHomePage(title: 'GRUPO 5 - 6SC'), // Establece la pantalla principal con el título del grupo.
    ); // Finaliza la configuración de MaterialApp.
  } // Finaliza el método build.
} // Finaliza la clase MyApp.

// Esta clase representa la pantalla donde el usuario escribe su nombre.
class MyHomePage extends StatefulWidget { // Crea un widget con estado porque su contenido puede cambiar.
  const MyHomePage({super.key, required this.title}); // Define el constructor y solicita obligatoriamente un título.
  final String title; // Declara una variable que almacena el título de la pantalla.

  @override // Indica que se sobrescribe el método createState.
  State<MyHomePage> createState() => _MyHomePageState(); // Crea el estado que controla los cambios de esta pantalla.
} // Finaliza la clase MyHomePage.

// Esta clase administra los datos y las acciones de la pantalla.
class _MyHomePageState extends State<MyHomePage> { // Define el estado asociado a MyHomePage.
  final TextEditingController _controller = TextEditingController(); // Crea un controlador para obtener el texto ingresado por el usuario.
  String _resultado = ''; // Declara una variable para almacenar el mensaje que se mostrará en pantalla.

  // Esta función procesa el nombre y genera el saludo correspondiente.
  void _saludar() { // Declara el método que se ejecuta al presionar el botón.
    String nombre = _controller.text; // Obtiene el nombre escrito en el campo de texto.
    if (_controller.text.trim().isEmpty) { // Comprueba que el campo no esté vacío ni contenga solamente espacios.
      setState(() { // Notifica a Flutter que debe actualizar la interfaz.
        _resultado = 'INGRESAR LOS NOMBRES COMPLETOS'; // Muestra un mensaje si el usuario no escribió su nombre.
      }); // Finaliza la actualización del estado.
      return; // Detiene la función para evitar generar un saludo vacío.
    } // Finaliza la condición de validación.
    setState(() { // Actualiza el estado para mostrar el saludo.
      _resultado = 'Hola $nombre. Bienvenidos a la UAE'; // Construye el saludo utilizando el nombre ingresado.
    }); // Finaliza la actualización del estado.
  } // Finaliza el método _saludar.

  @override // Indica que se sobrescribe el método build de la clase State.
  Widget build(BuildContext context) { // Construye la interfaz visual de la pantalla.
    return Scaffold( // Proporciona la estructura básica de la pantalla.
      appBar: AppBar( // Crea la barra superior de la aplicación.
        backgroundColor: Theme.of(context).colorScheme.inversePrimary, // Obtiene un color del tema para el fondo de la barra.
        title: Text(widget.title), // Muestra el título recibido desde MyHomePage.
      ), // Finaliza la barra superior.
      body: Padding( // Agrega un espacio alrededor del contenido principal.
        padding: const EdgeInsets.all(16), // Establece un margen interno de 16 unidades en todos los lados.
        child: Column( // Organiza los elementos de la interfaz verticalmente.
          crossAxisAlignment: CrossAxisAlignment.center, // Centra horizontalmente los elementos de la columna.
          children: [ // Define los elementos que aparecerán dentro de la columna.
            const Text("INGRESAR LOS NOMBRES COMPLETOS--"), // Muestra una indicación para que el usuario escriba su nombre.
            const SizedBox(height: 16.0), // Agrega un espacio vertical de 16 unidades.
            TextField(controller: _controller), // Crea el campo de texto y lo conecta con el controlador.
            const SizedBox(height: 16.0), // Agrega una separación antes del botón.
            ElevatedButton( // Crea un botón que permite ejecutar una acción.
              onPressed: _saludar, // Ejecuta la función _saludar cuando se presiona el botón.
              child: const Text('Saludar'), // Establece el texto que aparece dentro del botón.
            ), // Finaliza la configuración del botón.
            const SizedBox(height: 16.0), // Agrega una separación antes del resultado.
            Text(_resultado), // Muestra el mensaje de saludo o validación en pantalla.
          ], // Finaliza la lista de elementos de la columna.
        ), // Finaliza la columna.
      ), // Finaliza el espacio interno del contenido.
    ); // Finaliza la estructura Scaffold.
  } // Finaliza el método build.
} // Finaliza la clase _MyHomePageState.
