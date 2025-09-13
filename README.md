# 🧮 Convertidor de Bits

Aplicación de escritorio hecha en **Java Swing** que permite **convertir entre diferentes unidades de almacenamiento digital**: Bits, Bytes, Kilobytes, Megabytes, Gigabytes y Terabytes.

## 📋 Características

- Interfaz gráfica amigable con menús desplegables.
- Conversión entre:
  - Bits
  - Bytes
  - KiloBytes
  - MegaBytes
  - GigaBytes
  - TeraBytes
- Campo para introducir la **cantidad a convertir**.
- Botón **Calcular** para realizar la conversión.
- Botón **Borrar** para limpiar los campos.

## 🖼️ Interfaz principal

- `Unidad`: selección de la unidad de entrada.
- `Convertira`: selección de la unidad de salida.
- `Cantidad`: campo de texto donde el usuario escribe el valor numérico a convertir.
- `Resultado`: campo de texto donde se muestra el resultado después de presionar el botón Calcular.
- `Calcular (BotonConvertir)`: ejecuta la conversión.
- `Borrar (BotonConvertir1)`: limpia los campos de entrada y salida.

---

## ⚙️ Funcionamiento del botón Calcular (`BotonConvertir`)

Cuando el usuario presiona el botón **Calcular**, se ejecuta el método:

```java
private void BotonConvertirActionPerformed(java.awt.event.ActionEvent evt) {
    try {
        double cantidad = Double.parseDouble(Cantidad.getText());
        int unidadIndex = Unidad.getSelectedIndex();
        int convertirIndex = Convertira.getSelectedIndex();
        double[] factores = {1.0/8, 1, 1024, 1024*1024, 1024*1024*1024, 1024L*1024*1024*1024};

        // Convertimos la cantidad ingresada a Bytes
        double cantidadEnBytes = cantidad * factores[unidadIndex];
        double resultadoFinal = cantidadEnBytes / factores[convertirIndex];
        Resultado.setText(String.valueOf(resultadoFinal));
    } catch (NumberFormatException e) {
        Resultado.setText("Ingrese un número válido");
    }
}

## 🧠 Explicación paso a paso

### Obtención de datos de entrada
- Se toma el número que el usuario escribió en el campo `Cantidad`.
- Se obtienen los índices seleccionados en los `JComboBox` `Unidad` (unidad origen) y `Convertira` (unidad destino).

### Definición de factores de conversión
- El arreglo `factores` indica cuántos **Bytes equivale 1 unidad** de cada tipo.
- El orden es: Bits → Bytes → KB → MB → GB → TB.
- Ejemplo: `1.0/8` significa que 1 bit es 1/8 de byte.

### Conversión a Bytes como unidad base
- Se multiplica la cantidad ingresada por el factor correspondiente a la unidad de entrada, para obtener el valor en **Bytes**.

### Conversión a la unidad de destino
- Se divide el valor en Bytes entre el factor de la unidad de destino para obtener el resultado convertido.

### Mostrar resultado
- Se convierte el resultado a texto y se muestra en el campo `Resultado`.

### Manejo de errores
- Si el valor en `Cantidad` no es un número válido, se captura la excepción `NumberFormatException` y se muestra el mensaje `"Ingrese un número válido"`.

---

## 🗑️ Funcionamiento del botón Borrar

El botón **Borrar** simplemente vacía los campos de entrada y resultado:

```java
private void BotonConvertir1ActionPerformed(java.awt.event.ActionEvent evt) {
    Resultado.setText("");
    Cantidad.setText(" ");
}


