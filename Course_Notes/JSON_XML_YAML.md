# 60. JSON, XML, and YAML

## Data Serialization

- DATA SERIALIZATION is the process of converting DATA into a standardized format/structure that can be stored (in a file) or transmitted (over a network) and reconstructed later (ie: by a different application)
    - This allows the DATA to be communicated between applications in a way both APPLICATIONS understand.

- DATA SERIALIZATION languages allow us to represent *variables* with text

![image](remote_assets/f09eeeba-7779-40c8-af18-f1227bf0cf47.png)

---

## JSON (Javascript Object Notation)

- JSON (JAVASCRIPT OBJECT NOTATION) **is an open standard FILE FORMAT and DATA INTERCHANGE FORMAT that uses human-readable text to store and transmit data objects

- It is standardized in RFC 8259 (https://datatracker.ietf.org/doc/html/rfc8259)
- It was derived from JavaScript, but it is language-independent and many modern programming languages are able to generate and read JSON data
    - REST APIs often use JSON
- *Whitespace* is insignificant

- JSON can represent FOUR “primitive” DATA Types:
    - String
    - Number
    - Boolean
    - Null

- JSON also has TWO “structured” DATA Types:
    - Object
    - Array

---

### **JSON Primitive Data Types**

- A STRING is a text value. It is surrounded by double quotes “ “
    - “Hello”
    - “Five”
    - “5”

- A NUMBER is a numeric value. It is NOT surrounded by quotes
    - 5
    - 100
    
- A BOOLEAN is a DATA Type that has only TWO possible values, not surrounded by quotes
    - true
    - false

- A NULL value represents the intentional absence of any object value. It is not surrounded by quotes
    - null

---

### **JSON Structured Data Types**

- An OBJECT is an unordered list of *key-value pairs* (variables)
    - Sometimes called a DICTIONARY
    - OBJECTS are surrounded by curly brackets {}
    - The *key* is a STRING
    - The *value* is any valid JSON DATA Type (string, number, boolean, null, object, array)
    - The *key* and *value* are separated by a colon :
    - If there are multiple key-value pairs, each pair is separated by a comma

![image](remote_assets/24a15571-bb9f-43b4-889f-69f23ffb91bc.png)

![image](remote_assets/b66f041d-2449-43f0-8a04-2c0da5391411.png)

![image](remote_assets/54d69eed-4369-4ef6-a437-6b5ecce14586.png)

- An ARRAY is a series of *values* separated by commas
    - Not *key-value pairs*
    - The values do NOT have to be the same DATA Type

![image](remote_assets/3212f472-f966-49e5-9b9a-7bedcfe47487.png)

![image](remote_assets/f8075e93-2be7-4b2e-a2af-968961bbc5a7.png)

---

## XML (Extensible Markup Language)

- XML (EXTENSIBLE MARKUP LANGUAGE) was developed as a MARKUP language, but is now used as a general data serialization language
    - Markup languages (ie: HTML) are used to format text (font, size, color, headings, etc)
    - XML is generally less human-readable than JSON
    - Whitespace is insignificant
    - Often used by REST APIs
    - <key> value </key> (similar to HTML)

![image](remote_assets/f954b0ef-f563-4536-94c8-334b6d8f97c6.png)

![image](remote_assets/948dae9e-b59b-4607-8e6d-b39837baba70.png)

---

## YAML (YAML Ain’T Markup Language)

- YAML originally meant *YET ANOTHER MARKUP LANGUAGE* but to distinguish its purpose as a data-serialization language rather than a markup language, it was repurposed to *YAML AINT MARKUP LANGUAGE*
- YAML is used by the network automation tool ANSIBLE (covered later in the course)
- YAML is VERY Human-Readable
- Whitespace **is significant** (unlike JSON and XML)
    - Indentation is very important
- YAML files start with - - - (three dashes)
- - is used to indicate a list
- Keys and Values are represented as key : value

![image](remote_assets/ecfa3659-4bc3-4596-9f11-10d2644eac1a.png)

COMPARISON BETWEEN JSON and YAML using the same DATA

![image](remote_assets/16e0e98b-5653-4f8a-a388-1706f91a30d4.png)
