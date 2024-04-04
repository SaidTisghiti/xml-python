# xml-python

# DOM
## Definició
El **DOM** __(Document Object Model)__ es una interfaz de programación que nos permite crear, modificar y manipular documentos HTML y XML. Es una representación estructurada del documento, donde cada elemento del documento es un objeto dentro del modelo. El DOM facilita el acceso y la manipulación de los elementos del documento, como etiquetas HTML, atributos y contenido.
DOM significa Document Object Model. 
## Api
## Comandes principals

## Exemple fet a classe
```
<?xml version="1.0" encoding="UTF-8"?>
<universitat>
  <persona>
    <nom>Anna</nom>
    <cognoms>Garcia</cognoms>
    <edat>22</edat>
    <assignatures>
      <assignatura>Matemàtiques</assignatura>
      <assignatura>Física</assignatura>
      <assignatura>Química</assignatura>
      <assignatura>Biologia</assignatura>
    </assignatures>
  </persona>
  <persona>
    <nom>Carles</nom>
    <cognoms>Pérez</cognoms>
    <edat>30</edat>
    <assignatures>
      <assignatura>Química</assignatura>
      <assignatura>Biologia</assignatura>
    </assignatures>
  </persona>
  <persona>
    <nom>Marc</nom>
    <cognoms>Ruiz</cognoms>
    <edat>24</edat>
    <assignatures>
      <assignatura>Matemàtiques</assignatura>
      <assignatura>Física</assignatura>
      <assignatura>Química</assignatura>
      <assignatura>Informàtica</assignatura>
      <assignatura>Enginyeria</assignatura>
    </assignatures>
  </persona>
</universitat>
```
# 
## Definició

## Comandes principals

## Exemple fet a classe
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
# Python
## Definició
**Python** es un lenguaje de programación ampliamente utilizado en aplicaciones web, desarrollo de software, ciencia de datos y aprendizaje automático. Es un lenguaje de programación multiparadigma, lo que significa que no fuerza a los programadores a adoptar un estilo particular de programación.
## Comandes principals

## Exemple fet a classe

Fet per Saïd Tisghiti EL Kabbouti
