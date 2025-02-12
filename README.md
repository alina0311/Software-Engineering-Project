# Proiect IoT - Purificator Smart

Acest proiect este realizat in cadrul cursului de Inginerie Software, impreuna cu [Alina Dorneanu](https://github.com/alina0311) , [Gabriel Badescu](https://github.com/BadescuGabi) , [Radu Negulescu](https://github.com/radunegulescu) si [Irina Pavalasc](https://github.com/IrinaPavalasc).

In cadrul lui vom dezvolta partea de back-end a unui purificator smart ce are urmatoarele functionalitati:

- înregistrare si logare în aplicație
- crearea unui profil al utilizatorului (va răspunde la diverse întrebări: vârstă, sex, oraș, afecțiuni, program de funcționare al device-ului)
- crearea de moduri speciale 
- integrare de API pentru fum, nivel CO, NO2, SO2, O3
- jocuri de lumini
- notificari privind depasirea valorilor medii (personalizate in functie de afectiuni)
- pornirea unor alarme în cazul depășirii anumitor parametri
- pornirea automată pe baza unui program stabilit

Implementarea proiectului se va realiza in Java.

Link catre documentul de analiza: https://docs.google.com/document/d/1zegxxW3Ma2Hy8idONQcIOMgB3yz-dOM4IdGJO5W8LvM/edit#

## Documentare
Aplicatia expune un Rest **API HTTP** – documentat folosind Open API ([Swagger](http://localhost:8080/swagger-ui.html#/demo-application)) si un **API MQTT** – documentat folosind  [AsyncAPI](asyncapi.yaml)

## Instalare
Ca sistem de build e folosit **Maven**. 
Pentru configurația MQTT:
- instalarea _mosquitto_ (broker MQTT). Pentru download [apasa aici](https://mosquitto.org/download/)
- în folder-ul în care s-a descărcat mosquitto se va crea un fișier _broker.conf_ cu următorul conținut:
_listener 1883
allow_anonymous true_
- într-un CMD cu rol de administrator se va introduce următoarea comandă: _mosquitto -v -c broker.conf_.
Pentru verificarea configurației, într-un CMD se poate introduce următoarea comandă: _mosquitto_pub -t mytopic -m "Hello world"_ și mai apoi, se introduce următoarea comandă în alt CMD: _mosquitto_sub -t mytopic_. Dacă în fereastra de subscribe se afisează "Hello world", configurația este corectă și conexiunea a fost realizată de către broker. 


## Utilizare
Trebuie deschis urmatorul link: [Swagger](http://localhost:8080/swagger-ui.html#/demo-application).
Înainte de trimiterea request-urilor va apărea un pop-ul în care utilizatorul va trebui să introducă un username și o parolă. Pentru testare se poate folosi următorul mock user:
username **admin1** și password **123456**.
Dacă purificatorul utilizatorului nu este pornit, alte request-uri nu vor funcționa, așa că va trebui trimis request-ul _/pickOnSchedule_.
Apoi se pot trimite celelalte request-uri.

## Testare
Avem unit tests si integration tests.
