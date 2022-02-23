# ESI - ATTENDANCE 

## Seeder order
php artisan db:seed
- StudentSeeder
- GroupSeeder
- LiaisonStudentGroup
- ProfSeeder
- CourseSeeder
- PaeSeeder
- SeanceSeeder

## How to populate DB

 - To fill the db u must first upload an ICS file of "Cours" then a csv file with the Student, if u add new ICS file u must re-add CSV with         students.
 - The only ICS file that we manage are the "Cours" one, every other file wont work.
 - To add student use a CSV file
 
## Heroku

### How to use heroku :
- create an application in heroku;
#### in the terminal positionned in the app directory
- init your repository with the laravel app;
- add the postgreSQL addons with heroku :  
```
heroku addons:create heroku-postgresql:hobby-dev
```
- open the heroku bash
```
heroku run bash
```
- in the bash run the migrate and the seeds

```
php artisan migrate/db:seed ...
```
## When a push conflict occur
- remove all the file from the repository 
```
git rm -r * 
```
- add and push in order to get a clean repository
- copy the project inside the git repository 
- git add/commit/push ...


## Admin
### Make sure to update the composer
```
composer update
```
### Make sure to migrate the admin database table
```
php artisan admin:install
```
## What's done

- Heroku
- Consulter la liste
- Import des fichiers groupe
- La prise des présences
- Supression d'élève
- Import fichier horaire
- Ajout d'élève
- Ajouter fichier horaire dans la db
- Schéma de la DB
- Admin pane
- Import Étudiants via CSV
- Calendar
- Auth

## What we are working on

 - /

## Website

http://lit-atoll-02597.herokuapp.com/

## What has failed

- Test sur heroku (HEROKU CI est [payant](https://blog.heroku.com/heroku-ci-now-available))

## Schéma de la base de donnée
les différentes tables  
- Student
`un étudiant a un PAE et est associé à un groupe`
- Pae
`PAE est le programme annuel de l'étudiant qui appartient a un'étudiant etcontient  tous les cours qu'il devra suivre durant l'année`
- Teacher
`un teacher donne cour durant une séance et prend des présences liées aux étudiants d'un groupe`
- Course
`un cour et inscrit dans un Pae et est dispendé durant une séance`
- Liaison_Student_Group
`la liaison entre un groupe et un étudiant permet d'avoir plusieurs  étudiant dans un groupe et plusieurs  groupes pour un étudiant`
- Group
`un groupe a une seule liaison avec un étudiant et un groupe suit un cour à un moment donné`
- Seance
`une séance de cour est donné par un teacher à un ou plusieurs groupes et permettant à un teacher de dire quels étudiants étaient présents`
- Attendance
`Attendance est une table qui nous donnera la liste des présences des étudiants durant une séance de cour.`


## Utilisation Api google  

- Ajouter Socialite :  
```
composer require laravel/socialite  
```  

- Créé un compte google dans le cloud de google pour avoir l'accès à leur api de connexion:  
```
https://console.cloud.google.com/  
```
- Dans Api & service, dans l'onglet client  OAuth créé un projet et le nommé puis ajouter une url de redirection.  
Tous est affiché dans tableau de bord  

- dans l'application config, ajouter l'id du client et le client_secret généré par google et l'url de redirection.  
```
    'google' => [
        'client_id'     => 'mettre l'id  ',
        'client_secret' => ' ',
        'redirect' => ' ',    
    ],
```  
## ajouter les packages pour le QrCode  
  
  - Installer simple-qrcode Package  
  ```
  composer require simplesoftwareio/simple-qrcode

  ```  
  - Dans le dossier "config/app.php", ces lignes devraient être présentes :  
 ```  
  'providers' => [
    ....
    SimpleSoftwareIO\QrCode\QrCodeServiceProvider::class
],
'aliases' => [
    ....
    'QrCode' => SimpleSoftwareIO\QrCode\Facades\QrCode::class
],
 ```  
 - créé une route de redirction vers le qrcode et une page associée.

 ### if php artisan serve / composer update error occur 
 - in xampp/php/php.ini uncomment the line : "extension=gd"
 - run composer require simplesoftwareio/simple-qrcode


