Utilizarea containerelor ca medii de execuție

Scop

Această lucrare de laborator are ca scop familiarizarea cu comenzile de bază ale OS Debian/Ubuntu. De asemenea, aceasta va permite să vă familiarizați cu Docker și comenzile sale de bază.

Sarcina

Pornind de la imaginea oficială a sistemului de operare Ubuntu, să se creeze un container care să conțină un server web Apache. Să se creeze o pagină web care să conțină textul "Hello, World!" și să se afișeze într-un browser.

Executare

Am creat un nou repository containers03 și il clonam pe computer.

Pornire și testare

Deschidem terminalul în directorul containers03. Se rulează următoarea comandă pentru a porni un container Ubuntu cu numele containers03:

docker run -ti -p 8000:80 --name containers03 ubuntu bash

![420670208-db2adfab-052c-42b5-b209-bf2a7ac363e4](https://github.com/user-attachments/assets/bcce89bc-cbe5-492b-b13c-0137f6e58d4d)

Aceasta creează un container bazat pe imaginea Ubuntu, redirecționează portul 80 al containerului către portul 8000 al gazdei și deschide un terminal interactiv (-ti).

Se execută următoarele comenzi pentru actualizarea pachetelor și instalarea serverului Apache:

apt update

![420670312-49a6ea57-99bf-411d-8e75-d0fce26f68c5](https://github.com/user-attachments/assets/943eb09f-1afb-4671-ba79-41598c998fc1)

apt install apache2 -y

![420670373-cc21192a-962b-4538-9445-ca093851976b](https://github.com/user-attachments/assets/3444a9a1-6597-41a1-a65d-0c61122b0a66)

apt update actualizează lista de pachete disponibile, permițând instalarea celor mai recente versiuni.

apt install apache2 -y instalează serverul web Apache fără a solicita confirmare de la utilizator (-y).

Se pornește serverul Apache folosind comanda:

service apache2 start

![420670394-d817901b-c9ff-4388-ba60-96f2aa8c7133](https://github.com/user-attachments/assets/21ccd025-7b60-454d-95e3-53badd17c3d7)

Aceasta inițializează serviciul Apache pentru a accepta conexiuni web.

Deschidem browserul și introducem în bara de adrese http://localhost:8000.

![420670481-1a43f859-7918-4cb9-982f-8fd13a82b348](https://github.com/user-attachments/assets/28c5c626-6a6d-491a-a9b7-0bcef6d976b5)

Se listează conținutul directorului web root Apache:

ls -l /var/www/html/

![420670549-b2cb6e23-d5f8-4386-901b-5a50c3a451fb](https://github.com/user-attachments/assets/03d4863e-cb39-4559-a981-024bdd026666)

Această comandă afișează permisiunile, proprietarul și dimensiunea fișierelor din directorul web.

Se creează fișierul index.html cu următorul conținut:

![420670582-4cde5d79-50ce-48be-a0a5-12fb3f552dc9](https://github.com/user-attachments/assets/e6611723-0d02-42d1-9230-7446d7ef68a3)

Se reîmpreospeate păgina web pentru a vedea schimbările.

![420670613-ea58c0a1-4887-4f66-9b2c-9998720ea741](https://github.com/user-attachments/assets/af0a599c-ed07-44f1-9392-1c2db1fc7980)

Aceasta înlocuiește conținutul fișierului index.html cu textul HTML specificat.

Se verifică configurația serverului Apache:

cd /etc/apache2/sites-enabled/

![420670731-9bec1426-d59a-4a0c-a7df-1932afd07fda](https://github.com/user-attachments/assets/dbd57db8-d5e8-4635-a46b-bd77cc405b7b)

cat 000-default.conf

![420671101-76ec65b1-2cbe-43eb-84b7-96361a7a5c62](https://github.com/user-attachments/assets/864e3e43-cfa9-4127-8dad-943663f78b91)

cd /etc/apache2/sites-enabled/ schimbă directorul către locația fișierelor de configurare a site-urilor Apache.

cat 000-default.conf afișează conținutul configurației implicite, incluzând DocumentRoot și setările virtual host.

Inchidem fereastra terminalului cu comanda exit.

![420671135-5044854a-7036-498d-a9f7-13f3741a25e1](https://github.com/user-attachments/assets/1af34976-72da-4af1-bb03-993a191fddc6)

Se afișează lista de containere pentru a verifica existența containerului:

![420671151-ae96c920-190b-4a70-a586-97b822bc5a1f](https://github.com/user-attachments/assets/c677b508-bc1d-418f-bc83-15dbcee5d9dc)

Aceasta listează toate containerele, inclusiv cele oprite. Coloanele afișate includ ID-ul containerului, imaginea utilizată, starea și timpul de rulare.

Stergem containerul:

![420671258-2cd3b813-81ff-4fc1-9a13-71d4cde88dc7](https://github.com/user-attachments/assets/017fff6b-ab8d-4b8d-b526-44e514ebd4cc)

Aceasta elimină definitiv containerul containers03.

Concluzii

Această lucrare de laborator a demonstrat utilizarea Docker pentru crearea și gestionarea unui mediu izolat bazat pe Ubuntu, instalarea și configurarea serverului Apache și crearea unei pagini web simple. Prin aceste pași, s-a evidențiat importanța containerizării în dezvoltarea și testarea aplicațiilor web.
