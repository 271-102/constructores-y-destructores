# constructores-y-destructores
casandra
# archivo_temporal.py

import os
import time

class ArchivoTemporal:
    """
    Esta clase simula la creación de un archivo temporal.
    Usa el constructor __init__ para inicializar los atributos
    y el destructor __del__ para realizar la limpieza (borrado del archivo).
    """

    def __init__(self, nombre):
        """
        Constructor que se ejecuta al crear una nueva instancia de la clase.
        Aquí se inicializa el nombre del archivo y se simula su creación.
        """
        self.nombre = nombre
        print(f"[INFO] Creando el archivo temporal: {self.nombre}")
        with open(self.nombre, 'w') as f:
            f.write("Este es un archivo temporal.\n")

    def mostrar_contenido(self):
        """
        Método para leer y mostrar el contenido del archivo.
        """
        print(f"[INFO] Leyendo el archivo: {self.nombre}")
        with open(self.nombre, 'r') as f:
            print(f.read())

    def __del__(self):
        """
        Destructor que se ejecuta automáticamente cuando el objeto es destruido.
        Aquí se borra el archivo temporal si existe.
        """
        if os.path.exists(self.nombre):
            os.remove(self.nombre)
            print(f"[INFO] Archivo {self.nombre} eliminado en el destructor.")
        else:
            print(f"[WARN] Archivo {self.nombre} ya fue eliminado.")

# --- Uso del objeto ---

print("[MAIN] Iniciando el programa...")

archivo = ArchivoTemporal("temp.txt")
archivo.mostrar_contenido()

print("[MAIN] Terminando el programa...")
# Aquí el objeto 'archivo' se destruye automáticamente,
# y se llama al método __del__.

# También puedes forzar su destrucción usando:
# del archivo
