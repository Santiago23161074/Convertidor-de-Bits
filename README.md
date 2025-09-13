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

