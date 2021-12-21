# Arbeitsdokument Modell Lehrpläne

## Fehlende Attribute

- Darstellung von Materialverknüpfungen
- Verbindung mit Querschnittskompetenzen
- Dauer
- Inversionen von teaches und assesses?
    - Kompetenzen sollen auf Lehrmaterialien verweisen (grade verweisen Lehrmaterialien auf Kompetenzen) --> Issue erstellen
- `sameAs`: Zur Angabe der Relationen

## Mögliche Attribute und ihre Definition

- `@context` zur Verlinkung des [JSON-LD-Kontext-Dokuments](https://www.w3.org/TR/json-ld/#the-context)
- `id` zur Angabe der URL/URI einer Lernressource
- `type` zur Angabe des schema.org-Typs: hier sollte `Course` gesetzt werden
- [`name`](http://schema.org/name)
- [`description`](http://schema.org/description)
- [`about`](http://schema.org/about) (discipline):
    - bestenfalls mit Verweis auf bestehendes Vokabular, bspw.: https://vocabs.openeduhub.de/w3id.org/openeduhub/vocabs/discipline/index.html
- [`license`](http://schema.org/license)
- [`dateCreated`](http://schema.org/dateCreated)
- [`publisher`](http://schema.org/publisher)
- [`mainEntityOfPage`](http://schema.org/mainEntityOfPage): enthält ein Objekt mit der Beschreibung der Herkunft (`id` & [`provider`](http://schema.org/provider)), Erstellungs- ([`dateCreated`](https://schema.org/dateCreated)) und Änderungszeitpunkt ([`dateModified`](https://schema.org/dateModified)) sowie perspektivisch die Lizenz ([`license`](https://schema.org/license)) der Metadaten
- [`educationalLevel`](http://schema.org/educationalLevel):
    - [Definition des Vokabulars bei OpenEduHub](https://vocabs.openeduhub.de/w3id.org/openeduhub/vocabs/educationalLevel/index.html)
- [`oeh:educationalContext`](http://w3id.org/openeduhub/learning-resource-terms/)
    - dieses Vokabular bezeichnet das Bildungsumfeld, i.e. Kita, Grundschule
    - **das Property ist noch nicht offiziell definiert, weder auf schema.org, noch unter der genannten URL**
- [`hasPart`](http://schema.org/hasPart)
- [`isPartOf`](http://schema.org/isPartOf)
- [`dateModified`](http://schema.org/dateModified)
- [`version`](http://schema.org/version)
- [`keywords`](http://schema.org/keywords)


## Beispiel zur Abbildung in JSON(-LD):

```json
{
    "@context": {
        "@vocab": "http://schema.org/",
        "oeh": "http://w3id.org/openeduhub/learning-resource-terms/"
    },
    "id": "https://www.lehrplanplus.bayern.de/fachlehrplan/gymnasium/10/mathematik",
    "type": "Course",
    "name": "M10 5Fortführung der Raumgeometrie (ca. 22 Std.)",
    "description": "Die Schülerinnen und Schüler skizzieren Schrägbilder von Pyramiden und Kegeln, zeichnen zugehörige Netze und beschreiben diese Körper sowie ihre Grund- und Mantelflächen mit Fachbegriffen. erläutern, inwiefern man gerade Kreiszylinder, gerade Kreiskegel und Kugeln als Rotationskörper interpretieren kann. begründen die Formel zur Bestimmung des Oberflächeninhalts eines geraden Kreiskegels; sie verwenden dazu geeignete Skizzen. machen, ausgehend von geraden Prismen, z. B. mithilfe des Prinzips von Cavalieri plausibel, dass auch das Volumen eines schiefen Prismas gleich dem Wert des Produkts aus Grundflächeninhalt und Höhe ist. Sie machen die Struktur der Formel zur Bestimmung des Volumens einer Pyramide plausibel. machen die Formel zur Bestimmung des Volumens eines Kreiskegels plausibel, indem sie diesen Körper als Grenzfall von Pyramiden betrachten. machen die Struktur der Formeln zur Bestimmung des Volumens bzw. des Oberflächeninhalts einer Kugel plausibel. nutzen auch in Sachzusammenhängen zur Bestimmung von Volumina, Oberflächeninhalten, Längen und Winkelgrößen flexibel die bisher bekannten Volumen- und Oberflächeninhaltsformeln sowie geometrische Kenntnisse aus anderen Lernbereichen (insbesondere trigonometrische Zusammenhänge, Strahlensatz und Satz des Pythagoras). Ihre Lösungswege entwickeln sie dabei auf der Grundlage eines gewachsenen räumlichen Vorstellungsvermögens anhand von Überlegungen an geeigneten Skizzen, in einfachen Fällen auch im Kopf. Sie dokumentieren ihre Lösungswege nachvollziehbar, präsentieren sie fachsprachlich korrekt in ansprechender und überzeugender Form und beurteilen unterschiedliche Vorgehensweisen vergleichend.",
    "about": {
        "type": "DefinedTerm",
        "name": "Mathematik",
        "url": "http://w3id.org/openeduhub/vocabs/discipline/380",
        "inDefinedTermSet": "http://w3id.org/openeduhub/vocabs/discipline/"
    },
    "license": "https://creativecommons.org/publicdomain/zero/1.0/",
    "dateCreated": "2020-08-28",
    "publisher": {
        "type": "Organization",
        "url": "https://www.isb.bayern.de/",
        "name": "Staatsinstitut für Schulqualität und Bildungsforschung (ISB)"
    },
    "mainEntityOfPage": {
        "id": "https://source-of-metadata",
        "type": "Text",
        "provider": {
            "id": "https://www.isb.bayern.de/",
            "name": "Staatsinstitut für Schulqualität und Bildungsforschung (ISB)"
        },
        "license": "https://creativecommons.org/publicdomain/zero/1.0/",
        "dateCreated": "2020-01-01",
        "dateModified": "2020-02-02"
    },
    "educationalLevel": {
        "type": "DefinedTerm",
        "name": "10",
        "url": "http://w3id.org/openeduhub/vocabs/educationalLevel/10",
        "inDefinedTermSet": "http://w3id.org/openeduhub/vocabs/educationalLevel/"
    },
    "oeh:educationalContext": {
        "type": "DefinedTerm",
        "name": "Gymnasium",
        "url": "http://w3id.org/openeduhub/vocabs/educationalContext/gymnasium",
        "inDefinedTermSet": "http://w3id.org/openeduhub/vocabs/educationalContext"
    },
    "hasPart": "http://some-other-curriculums-data.com",
    "isPartOf": "http://w3id.org/openeduhub/curricula/curriculum_bayern/mathematik" ,
    "version": "1.0",
    "dateModified": "2020-06-28",
    "keywords": [
        "Mathematik",
        "Pythagoras"
    ]
}
```
