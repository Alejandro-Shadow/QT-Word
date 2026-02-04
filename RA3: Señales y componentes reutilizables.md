# RA3: Señales y componentes reutilizables

En esta práctica se integra el componente reutilizable WordCounterWidget en la aplicación MiniOffice, sustituyendo la lógica de conteo de palabras y caracteres.

## Componente WordCounterWidget

Archivo: contadorWidget.py

python
class WordCounterWidget(QWidget):
    conteoActualizado = Signal(int, int)
    Tipo de señal: Signal(int, int)

Parámetros emitidos:
conteoActualizado = Signal(int, int)
palabras (int): número total de palabras del texto.

caracteres (int): número total de caracteres del texto.

En VentanaPrincipal se conecta la señal a un slot:

self.contador_widget.conteoActualizado.connect(self.manejar_conteo_actualizado)

Slot correspondiente:

def manejar_conteo_actualizado(self, palabras: int, caracteres: int):
    self.barra_estado.showMessage(
        f"Texto actualizado: {palabras} palabras, {caracteres} caracteres",
        2000
    )


Cuándo se emite:
Cada vez que se llama a update_from_text(texto) y se recalculan los contadores interno

wpm (palabras por minuto): velocidad de lectura estimada.

mostrarPalabras: muestra u oculta la etiqueta de número de palabras.

mostrarCaracteres: muestra u oculta la etiqueta de caracteres.

mostrarTiempoLectura: muestra u oculta la etiqueta con el tiempo estimado de lectura.

parent: widget padre opcional.




Resumen

Incorporación de  WordCounterWidget en la barra de estado.

El conteo de palabras, caracteres y el tiempo estimado de lectura se realiza mediante el método update_from_text.

La aplicación se suscribe a la señal conteoActualizado(int, int) para reaccionar a los cambios que se produzcan en el texto.
