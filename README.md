# xml-python

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

<p align="center">
      <img src="https://github.com/Roxime13/Apunts-M4/assets/97622400/696bc789-52ca-4747-90d9-832bedc7507f" alt="imagenarbolhtml">
</p>
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
# 
## Definició

## Comandes principals

## Exemple fet a classe

# Python
## Definició
**Python** es un lenguaje de programación ampliamente utilizado en aplicaciones web, desarrollo de software, ciencia de datos y aprendizaje automático. Es un lenguaje de programación multiparadigma, lo que significa que no fuerza a los programadores a adoptar un estilo particular de programación.
## Comandes principals

## Exemple fet a classe

Fet per Saïd Tisghiti EL Kabbouti
