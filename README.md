# Proyecto Data Scientist
## Introducción
Python se ha convertido en el lenguaje líder en ciencia de datos gracias a:
### 1. **Ecosistema de Librerías Especializadas**
   - `Pandas` (manipulación de datos)
   - `NumPy` (cálculos numéricos)
   - `Matplotlib/Seaborn` (visualización)
   - `Scikit-learn` (machine learning)
   - `TensorFlow/PyTorch` (deep learning)
### 2. **Sintaxis Clara y Productiva**
   - Código legible que acelera el desarrollo
   - Ideal para prototipado rápido y análisis exploratorio
### 3. **Comunidad Activa y Recursos**
   - Amplia documentación y tutoriales
   - Soluciones a problemas comunes en Stack Overflow
### 4. **Integración con Herramientas Profesionales**
   - Compatibilidad con:
     - Jupyter Notebooks (análisis interactivo)
     - Bases de datos (SQL, MongoDB)
     - Big Data (PySpark, Dask)
Python se ha convertido en el lenguaje líder en ciencia de datos gracias a:
### 1. **Ecosistema de Librerías Especializadas**
   - `Pandas` (manipulación de datos)
   - `NumPy` (cálculos numéricos)
   - `Matplotlib/Seaborn` (visualización)
   - `Scikit-learn` (machine learning)
   - `TensorFlow/PyTorch` (deep learning)
### 2. **Sintaxis Clara y Productiva**
   - Código legible que acelera el desarrollo
   - Ideal para prototipado rápido y análisis exploratorio
### 3. **Comunidad Activa y Recursos**
   - Amplia documentación y tutoriales
   - Soluciones a problemas comunes en Stack Overflow
### 4. **Integración con Herramientas Profesionales**
   - Compatibilidad con:
     - Jupyter Notebooks (análisis interactivo)
     - Bases de datos (SQL, MongoDB)
     - Big Data (PySpark, Dask)

## Proyecto
El proyecto consiste en ayudar al señor Juan a decidir cuál de sus 4 tiendas tendría que vender para empezar un nuevo emprendimiento, para ello, nos proporcionan 4 archivos Excel, que contiene información relevante de cada tienda, como los productos que venden, sus categorías, ventas de cada producto, y valoraciones.

El primer paso para poder utilizar estos archivos y analizarlos con Python es importarlos, y utilizando pandas.

El código se ve de la siguiente forma:

```python
import pandas as pd

url = "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science-latam/refs/heads/main/base-de-datos-challenge1-latam/tienda_1.csv"
url2 = "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science-latam/refs/heads/main/base-de-datos-challenge1-latam/tienda_2.csv"
url3 = "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science-latam/refs/heads/main/base-de-datos-challenge1-latam/tienda_3.csv"
url4 = "https://raw.githubusercontent.com/alura-es-cursos/challenge1-data-science-latam/refs/heads/main/base-de-datos-challenge1-latam/tienda_4.csv"

tienda = pd.read_csv(url)
tienda2 = pd.read_csv(url2)
tienda3 = pd.read_csv(url3)
tienda4 = pd.read_csv(url4)

tienda.head()
```
## Cálculo de Facturación
Para calcular los datos de facturación es importante declarar 4 variables para cada tienda, donde almacenaremos el resultado de la suma de toda la casilla llamada "Precio", donde se encuentra la información del valor de todos los productos vendidos.
```python
# Ingreso total por cada tienda
total_tienda1 = sum(tienda["Precio"])
total_tienda2 = sum(tienda2["Precio"])
total_tienda3 = sum(tienda3["Precio"])
total_tienda4 = sum(tienda4["Precio"])

# Total de ventas por tienda
print("Total de ventas tienda 1: ", total_tienda1)
print("Total de ventas tienda 2: ", total_tienda2)
print("Total de ventas tienda 3: ", total_tienda3)
print("Total de ventas tienda 4: ", total_tienda4)
```
Es importante, para poder realizar la suma de las casillas, utilizar la función incorporada sum(), junto con esa función escribiremos una línea, sum(tienda["Precio"]), "tienda" es el nombre de la variable donde importamos el primer archivo Excel, que corresponde a la tienda 1, lo siguiente es escribir ["Precio"] que es ubicar la fila que queremos sumar, en este caso la fila tiene el nombre de "Precio".

## Categorías de Productos
Lo siguiente es calcular la cantidad de productos vendidos por categoría en cada tienda, por lo que en el código tendremos como objetivo agrupar los datos por categoría y contar el número de ventas de cada tipo, mostrando las categorías más populares de cada tienda.

El código se ve la siguiente forma:
```python
categoria = tienda.groupby("Categoría del Producto").size().sort_values(ascending=False)
categoria2 = tienda2.groupby("Categoría del Producto").size().sort_values(ascending=False)
categoria3 = tienda3.groupby("Categoria del Producto").size().sort_values(ascending=False)
categoria4 = tienda4.groupby("Categoria del Producto").size().sort_values(ascending=False)
```
Creamos una variable llamada categoría, una por cada tienda, la línea tienda.groupby nos ayudará a ubicar la fila objetiva, seguido de (“Categoría del Producto”).size(), esta línea es clave, ya que nos ayuda a contar las veces que se repite un elemento, por ejemplo, muebles, si observamos el Excel, esta categoría se repite varías veces, por los que .size() ubicará la fila de “Categorías del producto”) y contará los elementos, es decir, cuantas veces se repite “muebles”, “electrodomésticos”, etc. La siguiente línea. sort_values(ascending=False), nos permite ordenar la tabla de mayor a menor, es decir, a través de la cantidad que haya contado por categoría, ordenara y pondrá la categoría que más se repita, en pocas palabras la más vendida, y así sucesivamente con las demás categorías, este tipo de información es crucial para analizar que categoría es lo que más vende cada tienda, y la que menos vende, ya que la categoría menos vendida aparecerá al final de la tabla.

## Calificación promedio por tienda
Para realizar la calificación promedio por tienda, realizamos las siguientes líneas de código.
```python
promedio_tienda1 = sum(tienda["Calificación"]) / len(tienda["Calificación"])
promedio_tienda2 = sum(tienda2["Calificación"]) / len(tienda2["Calificación"])
promedio_tienda3 = sum(tienda3["Calificación"]) / len(tienda3["Calificación"])
promedio_tienda4 = sum(tienda4["Calificación"]) / len(tienda4["Calificación"])
```
Almacenamos nuestro resultado en variables que representarán el promedio de calificación por cada tienda.
La línea sum(tienda["Calificación"]), nos ubica en el Excel específicamente en la fila llama “Calificación”, y esta función sum() sumará todos los datos proporcionados en la fila, lo siguiente es realizar una división con el símbolo “/” seguido escribimos len(tienda["Calificación"]), esta línea, queremos saber la longitud de la fila, es decir cuanta información existe en dicha fila, por ejemplo, supongamos que en la fila calificación existen estos números: 4, 6, 8, 10. Lo que hará longitud es contar cuantos números hay en esa fila, en este ejemplo pequeño, hay solo 4 números, ahora, esta función “len()” nos ayudará a contar cuantos números existen, y es muy util para archivos con demasiada información. Una vez realizada la línea, estaríamos cumpliendo el objetivo de hacer un promedio de valoración de cada tienda.

## Producto más y menos vendido
Para poder realizar el producto más y menos vendido utilizamos las siguientes líneas de código
```python
vendidos_tienda1 = tienda.groupby("Producto").size().sort_values(ascending=False)
vendidos_tienda2 = tienda2.groupby("Producto").size().sort_values(ascending=False)
vendidos_tienda3 = tienda3.groupby("Producto").size().sort_values(ascending=False)
vendidos_tienda4 = tienda4.groupby("Producto").size().sort_values(ascending=False)
```
Está línea es igual a como se hizo el cálculo de las categorías más vendidas, las líneas de código funcionan igual, solo que en lugar de ubicar las líneas en “Categorías”, ubicamos la fila “Producto”, como se muestra a continuación en la siguiente línea, tienda.groupby("Producto").size().sort_values(ascending=False)
Aquí viene un paso muy importante, pues queremos mostrar 3 productos mas vendidos y 3 productos menos vendidos, para ello utilizamos las siguientes líneas
```python
print(f"Productos más vendidos tienda 1:\n{vendidos_tienda1.head(3)}\n\nProductos menos vendidos:\n{vendidos_tienda1.tail(3)}\n")
print(f"Productos más vendidos tienda 2:\n{vendidos_tienda2.head(3)}\n\nProductos menos vendidos:\n{vendidos_tienda2.tail(3)}\n")
print(f"Productos más vendidos tienda 3:\n{vendidos_tienda3.head(3)}\n\nProductos menos vendidos:\n{vendidos_tienda3.tail(3)}\n")
print(f"Productos más vendidos tienda 4:\n{vendidos_tienda4.head(3)}\n\nProductos menos vendidos:\n{vendidos_tienda4.tail(3)}\n")
```
En la concatenación de la función print, notamos estas dos funciones dentro de llaves, {vendidos_tienda1.head(3) y {vendidos_tienda1.tail(3)}, esto quiere decir que en nuestra variable que se almacenaron la cantidad de productos vendidos, con .head() nos mostrará los 3 primeros valores, es decir los valores más grandes, ya que la parte del código .sort_values(ascending=False) nos permite ordenar de mayor a menor, para {vendidos_tienda1.tail(), este nos mostrará los últimos valores, gracias a la función .tail(), agregamos un (3) en cada función, para mostrar los 3 primeros valores que encabezan la lista y los 3 últimos valores de la lista. (Nota importante: Estas dos funciones tomas lo que encabeza una fila y los últimos valores de la fila, esto no sabe diferenciar de un valor más grande o uno más chico, por lo que la línea .sort_values() se vuelve esencial para ordenar los valores, pues de no colocar esta línea, nuestra tabla sería “desordenada”)

## Costo de envío promedio
Para realizar los envíos promedios por tienda, calcularemos la media como se muestra en las siguientes líneas de código.
```python
promedio_envio_tienda1 = sum(tienda["Costo de envío"]) / len(tienda["Costo de envío"])
promedio_envio_tienda2 = sum(tienda2["Costo de envío"]) / len(tienda2["Costo de envío"])
promedio_envio_tienda3 = sum(tienda3["Costo de envío"]) / len(tienda3["Costo de envío"])
promedio_envio_tienda4 = sum(tienda4["Costo de envío"]) / len(tienda4["Costo de envío"])
```
Notamos que es muy similar a como se calculó las valoraciones por tienda, solo que la diferencia es la ubicación de la fila, en este caso, en lugar de ubicar a las líneas de código en la fila “Calificación”, la ubicaremos en la fila “Costo de envío”, sum(tienda["Costo de envío"]), y esta línea sumara todos los valores que existan en esa fila, seguido de la división entre la longitud de dicha fila con nuestra función len()

## Gráficos
Para mostrar gráficos, de todo nuestro análisis, utilizamos las siguientes líneas. 
```python
from matplotlib import pyplot as plt
tiendas = ["Tienda 1", "Tienda 2", "Tienda 3", "Tienda 4"]
#Graficos: Ingresos de las tiendas
ingresos = [total_tienda1, total_tienda2, total_tienda3, total_tienda4]
plt.bar(tiendas, ingresos)
```
Es importante importar pyplot desde matplotlib, para poder general gráficos, en este caso, agregamos dos variables, una llamada “tiendas” y agregamos un identificador por cada tienda, posteriormente lo agregamos a una lista, seguido de la variable “ingresos” que contiene una lista con las variables donde se encuentran almacena la información de facturación por cada tienda, la siguiente línea plt.bar(tiendas, ingresos), nos genera la grafica con la información proporcionada. 

La grafica se vería de la siguiente forma

![image](https://github.com/user-attachments/assets/8950a11e-0ab5-4a94-9336-a04756b01941)

Las siguientes líneas muestran como generar diferentes tipos de gráficos
```python
#Graficos: Opiniones de los clientes
calificaciones_total = [promedio_tienda1, promedio_tienda2, promedio_tienda3, promedio_tienda4]
plt.pie(calificaciones_total, labels=tiendas, autopct='%1.1f%%', startangle=90)
plt.title("Calificaciones de los clientes por tienda")
plt.axis('equal')
plt.show()
```
La grafica se vería de la siguiente forma:

![image](https://github.com/user-attachments/assets/6d971863-236d-4875-9eca-df3c7d1a0442)


```python
#Grafico de promedio total. 
promedio_envio_total_tienda = [promedio_envio_tienda1, promedio_envio_tienda2, promedio_envio_tienda3, promedio_envio_tienda4]
plt.fill_between(tiendas, promedio_envio_total_tienda, color='purple', alpha=0.5)
plt.plot(tiendas, promedio_envio_total_tienda, color='red', marker='o')
plt.title("Promedio total de envio por tiendas")
plt.xlabel("Tienda")
plt.ylabel("Promedio")
plt.grid(axis='y')
plt.show()
```
La grafica se vería de la siguiente forma

![image](https://github.com/user-attachments/assets/beea1bb7-0508-44a5-b57f-1d959244824f)
