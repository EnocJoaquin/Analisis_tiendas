# Analisis_tiendas

El documento es la realización de un proyecto de analisis de datos en que cual se evalua a tres tire tiendas con el fin de informar cual que la que vende menos. A continuación se muestra las lineas de codigo mas importantes que se realizaron en pandas.

#Total de ventas
se realizó la linea de codigo donde se suma el total de las ventas menos el total de costos de envio para obtener una ganancia neta

<p>
tienda['Precio'].sum()-tienda['Costo de envío'].sum()
</p>

#Ventas por categoría

En estas linea de codigo se agrupan los producto para divirdirlos en cada categoría y posteriormente se grafica 

<p>
productos_por_categoria = tienda.groupby('Categoría del Producto')['Producto'].count().reset_index()
productos_por_categoria.rename(columns={'Producto': 'Total de productos'}, inplace=True)
productos_por_categoria = productos_por_categoria.sort_values(by='Total de productos', ascending=False)
print(productos_por_categoria)

grafica_tienda = productos_por_categoria.plot.bar(x='Categoría del Producto', y='Total de productos', rot=90)
plt.show()
</p>

#Calificación promedio de la tienda

se obtiene el promedio de la columna calificación

<p>
  promedio_tienda = tienda['Calificación'].mean().round(2)
print(promedio_tienda)
</p>

#Productos más y menos vendidos

Se obtiene el numero de veces que mas y menos se repiten dentro de la columna Producto
<p>
productos_vendidos=tienda['Producto'].value_counts()
maximo_vendido = productos_vendidos[productos_vendidos == productos_vendidos.max()]
print(maximo_vendido)
minino_vendido = productos_vendidos[productos_vendidos == productos_vendidos.min()]
print(minino_vendido)
</p>
