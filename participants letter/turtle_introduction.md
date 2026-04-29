# Introduction to Turtle (TTL) for Knowledge Graphs

When we talk about the **Semantic Web** and **Knowledge Graphs**, we often need a way to describe data in a simple, structured form. One of the most widely used formats is **Turtle (TTL)**.

Turtle is short for *Terse RDF Triple Language*. Despite the long name, the idea is actually straightforward: it lets us write down information as **triples** — a subject, a predicate, and an object. Think of it as saying:

👉 **Thing – has property – value**

---

## 1. Describing Data as Triples

Let’s start small. Here’s a single triple in Turtle:

```ttl
ex:Book1  ex:title  "The Hobbit" .
```

This line says: **Book1 has the title “The Hobbit.”**

Notice the period (`.`) at the end — every triple ends with one.

---

## 2. Using Prefixes

Writing full web addresses (URIs) every time would be painful. That’s why Turtle uses **prefixes** to shorten them.

```ttl
@prefix ex: <http://example.org/> .

ex:Book1 ex:title "The Hobbit" .
```

Here, `ex:` stands for `http://example.org/`. So `ex:Book1` is just a shorthand.

---

## 3. Declaring Types

We often want to say *what kind of thing* something is. In Turtle, we use `a` for that.

```ttl
ex:Book1 a ex:Book .
```

This simply means: **Book1 is a Book.**

---

## 4. Adding More Details

A subject usually has more than one property. Turtle allows us to stack them neatly with semicolons:

```ttl
ex:Book1 a ex:Book ;
         ex:title "The Hobbit" ;
         ex:author "J.R.R. Tolkien" .
```

The semicolon (`;`) keeps the subject the same, so we don’t need to repeat `ex:Book1`.

---

## 5. Multiple Values

Sometimes one property has multiple values. For example, a book may belong to more than one genre:

```ttl
ex:Book1 ex:genre "Fantasy" , "Adventure" .
```

The comma separates multiple values for the same property.

---

## 6. Typed Values: Dates and Numbers

Not all data is plain text. Dates and numbers can be written with datatypes.

```ttl
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

ex:Book1 ex:published "1937-09-21"^^xsd:date ;
         ex:pages 310 .
```

Here:
- `"1937-09-21"^^xsd:date` means a date value.
- `310` is a number (no quotes needed).

---

## 7. Examples

A simple exaple:

the following text can be formulated as turtle :


There is a dataset about a book called “Harry Potter and the Sorcerer’s Stone.” This book was written by J.K. Rowling. The book was created on June 26, 1997. The subject of the book is fantasy. The dataset is related to a book review called “A Magical Start to a Beloved Series.” The review was published in 1997.

```ttl
@prefix ex:  <http://example.org/> .
@prefix dct: <http://purl.org/dc/terms/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

# A dataset about a book
ex:HarryPotterBook a dct:Dataset ;
    dct:title "Harry Potter and the Sorcerer's Stone" ;
    dct:creator ex:JkRowling ;
    dct:dateCreated "1997-06-26"^^xsd:date ;
    dct:subject "Fantasy Story" ;
    dct:relation ex:BookReview .

# The person who wrote it
ex:JkRowling a dct:Agent ;
    dct:title "J.K. Rowling" .

# A related book review
ex:BookReview a dct:BibliographicResource ;
    dct:title "A Magical Start to a Beloved Series" ;
    dct:issued "1997"^^xsd:gYear .
```

A Complete Knowledge Graph Example

Now let’s put everything together. We’ll describe a dataset, the person who created it, and a related publication.
There is a dataset called Dataset1.

Dataset1 is a dataset.

The title of Dataset1 is “Air Quality Data Berlin 2021.”

The creator of Dataset1 is Person1.

Dataset1 was created on September 10, 2021.

The subject of Dataset1 is “Environmental Data.”

Dataset1 is related to another resource called Publication1.

Person1 is an agent.

The title of Person1 is “Dr. Anna Müller.”

Publication1 is a bibliographic resource.

The title of Publication1 is “Air Pollution Trends in European Cities.”

Publication1 was issued in 2022.


```ttl
@prefix ex:  <http://example.org/> .
@prefix dct: <http://purl.org/dc/terms/> .
@prefix xsd: <http://www.w3.org/2001/XMLSchema#> .

# A dataset
ex:Dataset1 a dct:Dataset ;
    dct:title "Air Quality Data Berlin 2021" ;
    dct:creator ex:Person1 ;
    dct:dateCreated "2021-09-10"^^xsd:date ;
    dct:subject "Environmental Data" ;
    dct:relation ex:Publication1 .

# The person who created it
ex:Person1 a dct:Agent ;
    dct:title "Dr. Anna Müller" .

# A related publication
ex:Publication1 a dct:BibliographicResource ;
    dct:title "Air Pollution Trends in European Cities" ;
    dct:issued "2022"^^xsd:gYear .
```

---

✨ That’s Turtle in a nutshell: triples, prefixes, types, and a few handy separators (`.`, `;`, `,`).  
With these basics, you can describe almost anything in a structured, machine-readable way.
