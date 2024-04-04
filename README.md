# DOM
## Definicion
El **DOM** __(Document Object Model)__ es una interfaz de programación que nos permite crear, modificar y manipular documentos HTML y XML. Es una representación estructurada del documento, donde cada elemento del documento es un objeto dentro del modelo.
## API
Una **API** o __interfaz de programación de aplicaciones__ es un conjunto de definiciones y protocolos que se usa para diseñar e integrar el software de las aplicaciones.
## Nodos de DOM
Los nodos de DOM son etiquetas del cuerpo de un XML o HTML.
Hay dos tipos de nodos, los cuales son los siguientes:
1. Nodo de texto: Es el texto que hay dentro de las etiquetas.
2. Nodo de elemento: Son las etiquetas donde nosotros recorremos para encontrar en el árbol del XML o HTML.

Dentro de los nodos se classifican en base a una jerarquia, el qual son los siguientes:

1. Nodo padre: Es el principal nodo.
2. Nodo hijo: Son los nodos que estan debajo de los padres.
3. Nodo hermanos: Son los nodos hijos, que entre ellos se compaginan, son hermanos.

![imagen](/dom-document.jpg)

## Enlace de referencia para utilizar DOM en Python

[DOM](https://www.w3schools.com/xml/dom_intro.asp)

## Ejemplo hecho en clase usando minidom con python

```
from xml.dom import minidom

doc = minidom.parse("UF2A3.xml")

universitat=dict()

persona = doc.getElementsByTagName("persona")

for x in persona:
    noms=x.getElementsByTagName("nom")[0].firstChild.data
    cognoms=x.getElementsByTagName("cognoms")[0].firstChild.data
    nom_complert=(f"{noms} {cognoms}")
    assignatures=x.getElementsByTagName("assignatura")
    dades_assignatura=list()
    for cont, y in enumerate(assignatures):
        assignatura=x.getElementsByTagName("assignatura")[cont].firstChild.data
        dades_assignatura.append(assignatura)
    universitat[nom_complert]=dades_assignatura

continuar=True

while continuar:
    print("\nMenú:")
    print("1. Veure les notes de una persona.")
    print("2. Sortir")
    opcio=input("\nOpcio: ")
    if opcio=="1":
        print("\nLes persones que hi han a l'universitat son els seguents:")
        cont1=1
        for x, y in universitat.items():
            print(f"{cont1}. {x}")
            cont1+=1
        opcio=int(input("Quina opcio vols escollir: "))
        cont2=1
        for x, y in universitat.items():
            if cont2==opcio:
                print(f"\nLes asignatures que té {x} son els següents:")
                for z in y:
                    print(f"- {z}")
            cont2+=1
    elif opcio=="2":
        print("Has sortit correctament.")
        continuar=False
    else:
        print("Error!!!")
```

# XPath
## Definicion
**Xpath** o __(XML Path Language)__ es el sistema que se utiliza para navegar y consultar los elementos y atributos contenidos en la estructura de un documento XML.
## Tipos de expresiones
Para poder utilizarlo, hacen falta saber las expresiones para recorrer el arbol XML:
1. `/` Nodo arrel
2. `//` Todos los nodos que se encuentran debajo del actual
3. `@` Atributo
4. `<>` Elementos
5. `.` Nodo actual
6. `..` Nodo padre
7. `text()` Muestra el texto del nodo

![imagen](/imagen_2024-04-05_002202873.png)

## Enlace de referencia para utilizar DOM en Python

[XPath](https://www.w3schools.com/xml/xpath_intro.asp)

## Ejemplos vistos a clase

`/botiga/bluray[1]` indica el primer elemento bluray.
`//title[@idioma]` indica los titulos con atributo idioma.
`//title[@idioma=‘cat’]` indica los titulos con atributo idioma igual a cat.
`/botiga/bluray[preu>10]` indica todos los bluray con precio > 10.
`/botiga/bluray[preu>10]/any` indica todos los años de los bluray con precio > 10.
`/botiga/*/preu` indica todos los precios de los hijos de tienda.
`//*` indica todos los elementos del documento.
`//titol[@*]` indica todos los elementos titulo con cualquier atributo.
`//titol | // preu` indica todos los titulos y precios del documento.
`/botiga/bluray[2]/titol` indica el titulo del segundo bluray.
`/botiga/bluray[position()<6]/titol` indica el titulo de los 5 primeras entradas.

# XSLT
## Definicion
**XSLT** __(eXtensible Stylesheet Language for Transformations)__ es un lenguaje que permite aplicar una transformación a un documento XML para obtener otro documento XML, un documento HTML o un documento de texto plano.
## Elementos a utilizar en XSLT

1. El elemento `<xsl: template>` se utilitza para crear plantillas.
2. El elemento `<xsl: value-of>` se utilitza para extraer el valor de un nodo seleccionado.
3. El elemento `<xsl: for-each>` nos permite hacer bucles en XSLT.
4. El elemento `<xsl: for-each>` nos permite poner condiciones para que muestre solo aquellos datos que queremos mostrar.

## Enlace de referencia para utilizar DOM en Python

[XSLT](https://www.w3schools.com/xml/xsl_intro.asp)

## Ejemplo hecho en clase

```
<?xml version="1.0" encoding="UTF-8"?>
<xsl:stylesheet version="1.0" xmlns:xsl="http://www.w3.org/1999/XSL/Transform">
    <xsl:output method="html" indent="yes"/>
    <xsl:template match="/horari">
        <head>
            <style type="text/css">
                <xsl:for-each select="colors/color">
                    .<xsl:value-of select="@codi"/>{background-color: <xsl:value-of select="."/>; padding: 15px; margin: 2px;}
                </xsl:for-each>
                body{
                    background-color: rgb(197, 193, 193);
                    text-align: center;
                }
                table{
                    width: 100%;
                    text-align: center;
                    border-collapse: collapse;
                }
                th{
                    background-color: rgb(150, 144, 144);
                }
                li{
                    list-style-type: none;
                    padding: 6px;
                }
                a{
                    color: rgb(0,0,0);
                }
                img{
                    width: 100%;
                    height: 130px;
                }
            </style>
        </head>
        <html>
            <body>
                <img src="{@header}"/>
                <table>
                    <tr>
                        <xsl:for-each select="setmana/dia">
                            <th>
                                <xsl:value-of select="@nom"/>
                            </th>
                        </xsl:for-each>
                    </tr>
                    <tr>
                        <xsl:for-each select="setmana/dia">
                            <td>
                                <xsl:for-each select="modul">
                                    <p class="{codi}">
                                        <xsl:value-of select="codi"/>&#160;<xsl:value-of select="nom"/>
                                    </p>
                                </xsl:for-each>
                            </td>
                        </xsl:for-each>
                    </tr>
                </table>
                <ul>
                    <h1><xsl:value-of select="links/@nom"/></h1>
                    <xsl:for-each select="links/link">
                        <xsl:sort select="nom"/>
                        <li>
                            <a href="{url}">
                                <xsl:value-of select="nom"/>
                            </a>
                        </li>
                    </xsl:for-each>
                </ul>
            </body>
        </html>
    </xsl:template>
</xsl:stylesheet>
```

Fet per Saïd Tisghiti EL Kabbouti
