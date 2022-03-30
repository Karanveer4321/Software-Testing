# Assignment  1 (19103008)
Create Use-case and Sequence diagram using PLantUML tool.

## 1. Sequence Diagram
### Diagram
![Sequence Diagram](https://github.com/Karanveer4321/Software-Testing/blob/a17a06f2e2d1a6d183a772b1ceb3a080eca08874/Assignment%201/SequenceDiagram.png)

### Code
```
@startuml
actor User as user
participant "Login/Signup" as auth
participant "Home Page" as home
participant "Server" as server
participant "Favourites" as fav
participant "Trip Website" as trp
participant "Blog Websites" as blog

user -> auth : Enter UserName
auth -> server : Verify UserName
server -> auth : Request Password
user -> auth : Enter Password
auth -> server : Verify Password

alt If Password is valid
    server -> auth : Login Successful
else Else
    server -> auth : Invalid Credentials, please retry
end

server -> trp : Request data to fill in Form
trp -> server : Return data
server -> blog : Request data to fill in Blog
blog -> server : Return data
server -> home : Display content on screen
home -> fav : Add to favourites
fav -> server : Save in server

@enduml
```

## 2. UseCase Diagram
### Diagram
![UseCase Diagram](https://github.com/Karanveer4321/Software-Testing/blob/a17a06f2e2d1a6d183a772b1ceb3a080eca08874/Assignment%201/Usecase.png)

### Code
```
@startuml
left to right direction

actor User as user
actor WebServer as server

rectangle Amazon{
(Login) as login
(Create New Account) as register
(Verify Credentials) as verify
(Display Login Error) as error
(Apply Filters) as filters
(View Products) as viewProducts
(Add to favourites) as addfav
(Remove from favourites) as remfav
}

login ..> verify : include
register ..> verify : include
login <.. error : extend

user -- login
user -- register
user -- filters
user -- viewProducts
user -- addfav
user -- remfav
server -- filters
server -- viewProducts
server -- addfav
server -- remfav

@enduml
```
