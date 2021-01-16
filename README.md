# JSD
Jednostavan DSL koji služi za generisanje Spring Boot Rest Api aplikacija. Preciznije, ovaj jezik omogućava generisanje svih slojeva Spring Boot aplikacije, koji podrazumevaju: modele, kontrolere, repozitorijume i servise. 
U odnosu na model se generiše kontroler koji koristi funkcionalnosti konkretnog servisa koji zavisi od repozitorijuma. 

##Primer 1
```
entity Book
	isbn:  string -> {ID}, {};
	title: string;
	author: Author;
	controller -> "Books"
	
entity Author
	authorID: int -> {ID}, {};
	name:     string;
	lastname: string;
	controller -> "Authors"
```

##Primer 2
```
entity Book
	isbn:  string -> {ID}, {};
	title: string;
	author: Author;
	controller -> "Books"
	*GET -> title;
	*GET -> title/author;
	
entity Author
	authorID: int -> {ID}, {};
	name:     string;
	lastname: string;
	controller -> "Authors"
	*GET -> authorID;
```
