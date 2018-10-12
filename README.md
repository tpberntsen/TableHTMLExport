# TableHTMLExport V1.0.0
Plugin de *Jquery* que exporta una tabla HTML a JSON, CSV, TXT, o PDF y forzar al navegador a darcargar el archivo generado.

Jquery *plugin* that exports an HTML table to JSON, CSV, TXT, or PDF.

## Instalacion | Install

Puede descargar el archivo *tableHTMLExport.js* que esta en la carpeta *src* de este repositorioo o utilizar el CDN

You can download the *tableHTMLExport.js* file that is in the *src* folder of this repository or use the CDN

### CDN
```html
<script src="https://gitcdn.xyz/repo/FuriosoJack/TableHTMLExport/v1.0.0/src/tableHTMLExport.js"></script>
```

## Opciones | Options

- type: Opcion(string) para especificar el tipo de exportacion (csv,txt,json,pdf)
- separator: Opcion(string) que sera util solo cuando se exportar a *csv* en donde se especifica el caracter que servira como separador entre columnas *default: ,*
- newline: Opcion(string) que sera util solo cuando se exportar a *csv* en donde se especifica los caracteres para una nueva linea *default: \r\n*
- ignoreColumns: Opcion(string) para especificar el con los selectores de css de las columnas que se ignoraran *default: ''*
- ignoreRows: Opcion(string) para especificar los selectores de css de las columnas que se ignoraran *default: ''*
- htmlContent: Opcion(bool) para indicar si el contenido de la tabla a exportar tiene codigo HTML *default: false*
- consoleLog: Opcion(bool) para indicar si se quiere que se vean los logs del proceso de exportacion *default: false*
- trimContent: Opcion(bool) que sera util solo cuando se exporta a *csv* y la cual recorta el contenido de las etiquetas individuales *\<th>*, *\<td>*  de los espacios en blanco. Esto producirá una salida válida incluso si la tabla está sangrada *default: true*
- quoteFields Opcion(bool) que sera util solo cuando se exporta a *csv* y la cual cita campos *default: true*.
- filename: Opcion(string) nombre con el que el archivo se va a guardar *default: tableHTMLExport.csv*
# Ejemplo


```html
<table id="tableCompany">
  <thead>
    <tr>
      <th>Company</th>
      <th>Contact</th>
      <th class='acciones'>Country</th>
  </tr>    
  </thead>
  <tbody>
    <tr>
      <td>Alfreds Futterkiste</td>
      <td id="primero">Maria Anders</td>
      <td class="acciones">Germany</td>
    </tr>
    <tr>
      <td>Ernst Handel</td>
      <td>Roland Mendel</td>
      <td class="acciones">Austria</td>
    </tr>
    <tr>
      <td>Island Trading</td>
      <td>Helen Bennett</td>
      <td>UK</td>
    </tr>
    <tr id="ultimo">
      <td>Magazzini Alimentari Riuniti</td>
      <td>Giovanni Rovelli</td>
      <td>Italy</td>
    </tr>
  </tbody>  
</table>
```


## Exportar a JSON | Export To JSON

[Ejemplo Funcional](https://codepen.io/furiosojack/pen/JmyExX?editors=1111)

```javascript
$("#tableCompany").tableHTMLExport({type:'json',filename:'tablaLicencias.json',ignoreColumns:'.acciones,#primero',ignoreRows: '#ultimo'});
```

Resultado: tablaLicencias.json
```json
{
  "header": [
    "Company",
    "Contact"
  ],
  "data": [
    [
      "Alfreds Futterkiste"
    ],
    [
      "Ernst Handel",
      "Roland Mendel"
    ],
    [
      "Island Trading",
      "Helen Bennett",
      "UK"
    ]
  ]
}

```
## Exportar a CSV | Export To CSV

```javascript
$("#tableCompany").tableHTMLExport({type:'csv',filename:'tablaLicencias.csv',ignoreColumns:'.acciones,#primero',ignoreRows: '#ultimo'});
```
Resultado: 
```csv
"Company","Contact"
"Alfreds Futterkiste","Ernst Handel","Roland Mendel"
"Island Trading","Helen Bennett"
"UK",
```

## Exportar a PDF | Export To PDF
[Ejemplo Funcional](https://codepen.io/furiosojack/pen/gBxmvQ?editors=1111) 

Para exportar a PDF es requerido la libreria [jsPDF-AutoTable](https://github.com/simonbengtsson/jsPDF-AutoTable)

```javascript
$("#tableCompany").tableHTMLExport({type:'pdf',filename:'tablaLicencias.pdf',ignoreColumns:'.acciones,#primero',ignoreRows: '#ultimo'});
```

Resultado: 
![alt text][exporPDF]

[exporPDF]: https://image.ibb.co/kZvgB9/Captura.png "Como ser ve la exportacion PDF"



