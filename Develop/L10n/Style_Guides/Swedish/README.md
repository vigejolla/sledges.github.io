---
title: Swedish
permalink: Develop/L10n/Style_Guides/Swedish/

---

# Grammar

For example in short strings with stand-alone terms: **Jolla-konto**

Please however use them if a similar string/sentence in regular Swedish
would use an article: **Kunde inte logga in på kontot**

## Prepositions

When choosing objects in menus or lists, use the following prepositions
in Swedish:

  - Menu objects are **på en meny**:
      - Correct: **Välj Spara som på Arkiv-menyn.**
      - Incorrect: **Välj Spara som från Arkiv-menyn.**
      - Incorrect: **Välj Spara som i Arkiv-menyn.**
  - For lists, use the form **lista över**, not **lista på** or **lista
    med**:
      - Correct: **I fönstret visas en lista över alternativ.**
      - Incorrect: **I fönstret visas en lista på alternativ.**
      - Incorrect: **I fönstret visas en lista med alternativ.**
  - Logging into an account, server, site or app:
      - Correct: **Logga in på kontot/servern/webbplatsen.**
      - Correct: **Logga in i en app.**
      - Incorrect: **Logga in till kontot/servern/webbplatsen.**
      - Incorrect: **Logga in på en app.**
      - Incorrect: **Logga in till en app.**

For example:

  - Correct: **...gör du så här:**
  - Incorrect: **...gör man så här:**

## Colloquialisms

Do not use colloquialisms in the form of talspråk, e.g. **mej, dej, nåt,
nånting, sånt**. Also, do not use slang, as it might not be generally
understood.

When colloquialisms or idiomatic expressions are used in the source
text, do not translate them literally. Use the equivalent Swedish
expression. Example:

  - English: Kill two birds with one stone
  - Correct: **Slå två flugor i en smäll**
  - Incorrect: **Döda två fåglar med en sten**

## Tense

Use the present tense. E.g.:

  - Correct: **Media player väljer låtar**
  - Incorrect: **Media player kommer att välja låtar**

## Descriptive past tense forms in English

Very often, English source texts will use what looks like the past tense
in descriptive text. Example: When the form is submitted (meaning “when
you submit the form”, not “when you have submitted the form”) or When
the dialog is closed (meaning “when you close the dialog box”, not “when
you have closed the dialog box” or “when the dialog box has been
closed”).

This is not an indication of an action in the past, but rather a
description of an action that is carried out. The correct translation of
this in Swedish is not using the past tense, but rather the present
tense:

  - Correct: **När formuläret skickas** or **När du skickar
    formuläret**.
  - Incorrect: **När formuläret har skickats** or **När formuläret är
    skickad**.

<!-- end list -->

  - Correct: **När dialogrutan stängs** or **När du stänger
    dialogrutan**.
  - Incorrect: **När dialogrutan har stängts** or **När dialogrutan är
    stängd**.

For example:

  - Correct: **Ange kontoinställningar i**
  - Incorrect: **Kontoinställningar anges i**

For example:

  - Correct: **Gå till Inställningar**
  - Incorrect: **Användaren går till Inställningar**

## Usage of “Please” and other forms of politeness

When translating strings that use “Please”, etc. you should omit these
in Swedish. **Vänligen** and similar phrasings are to be avoided.

  - Correct: **Data hämtas. Vänta.**
  - Incorrect: **Data hämtas. Vänligen vänta.**

<!-- end list -->

  - Correct: **Ange dina inloggningsuppgifter.**
  - Incorrect: **Vänligen ange dina inloggningsuppgifter.**

<!-- end list -->

  - Correct: **Egenskaper för användare**
  - Incorrect: **Egenskaper för Användare**

Respect Swedish capitalization rules. We don’t use initial capitals for
nouns unless they refer to proper names or UI elements.

## Tone

The following table lists some examples of preferred phrasings to make
the tone “friendlier”.

| Classic word/phrasing                         | Preferred word/phrasing                                                                                                                                                     |
| --------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| erhålla                                       | *få*                                                                                                                                                                        |
| såväl … som                                   | *också, både … och*                                                                                                                                                         |
| ha möjlighet                                  | *kan*                                                                                                                                                                       |
| X gör det möjligt att …                       | *Med X kan du …*                                                                                                                                                            |
| dock, emellertid                              | ''men ''(example: *Det går inte att logga in på kontot. Du kan emellertid försöka igen senare.* vs. *Det går inte att logga in på kontot, men du kan försöka igen senare.*) |
| föregående                                    | *förra*                                                                                                                                                                     |
| nästföljande                                  | *nästa*                                                                                                                                                                     |
| såsom, exempelvis                             | *till exempel, som* (*NOTE: never combine these to form the phrasing ”som till exempel” or ”som exempelvis”)*                                                               |
| e-postmeddelande                              | *e-post*                                                                                                                                                                    |
| skicka e-post                                 | *skicka e-post*/*e-posta*                                                                                                                                                   |
| Mer information om hur du gör detta finns på… | *Få reda på hur du gör det här på …*                                                                                                                                        |
| skrivbordsunderlägg                           | *bakgrundsbild*                                                                                                                                                             |
| tillhandahålla                                | *ge, förse med*                                                                                                                                                             |
| i enlighet med                                | *enligt, utifrån, baserat på*                                                                                                                                               |

# Punctuation

## Hyphenation

Hyphenate when combing UI terms or acronyms with running text:

  - Correct: ***Arkiv*-menyn, ISO-certifiering**
  - Incorrect: ***Arkiv*menyn/*Arkiv* menyn, ISOcertifiering/ISO
    certifiering**

<!-- end list -->

  - Correct: **bilder** or **kartor**
  - Wrong: **bild(er)** or **karta(-or)**

## Series

Use a comma to separate elements in a series, but not the last two
elements.

  - Correct: **Du kan skapa nya, ändra eller ta bort objekt.**
  - Incorrect: **Du kan skapa nya, ändra, eller ta bort objekt.**

## Semi-colons

Avoid using semi-colons in Swedish. Try to break the text up into
smaller, individual sentences instead.

Do not start a heading with an article.

  - Correct: **Starta en app**
  - Incorrect: **Att starta en app**

Example: **På fliken *Inställningar*, gå till området *Avancerat* och
klicka på knappen *Ändra*. Då öppnas dialogrutan *Avancerade
inställningar*.**

## Personification of the software

In Swedish, neither the phone nor any software/app will have what can be
interpreted as a life of its own. Therefore, it will not take any own
initiatives. For example:

  - UK phrasing: The screen shows a list of users
  - Correct: **På skärmen visas en lista över användare**
  - Incorrect: **Skärmen visar en lista över användare**

<!-- end list -->

  - UK phrasing: The cell phone restarts
  - Correct: **Mobilen startas om automatiskt**
  - Incorrect: **Mobilen startar om automatiskt**

## Symbols

Do not use the "&" symbol in Swedish, please write "och" instead.

# Numerals

For example:

  - Correct: **1 message received**
  - Incorrect: **One message received**

Use a comma as a decimal separator and non-breaking space as thousands
separator: **15,7** and **10 000 kr**

## Measurements

Use numerals for measurements. Use a space between the numeral and the
unit, except with the degree symbol: **4 kg, 235 mm, 37,5 °C, 87 %,
90°**

# Fictitious content

Ensure that any fictitious names used in the translation are approved.
In most cases the names from the source text can be left as is as they
are often international names. Do not translate company names, example
domain names, e-mail and web addresses

# Terminology
