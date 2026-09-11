## 1.2 — Observer
### Q3 — Combien de documents ?

    8 indiqué à côté de l'onglet Documents

### Q4 — Le premier document

    Compass : filtre { }, tri { _id: 1 }, limit 1 (ou Skip 0)
    Query : db.books.find().sort({ _id: 1 }).limit(1)
    Réponse : "Le Petit Prince" (Antoine de Saint-Exupéry, 1943)

### Q5 — Le deuxième document

    Compass : tri { _id: 1 }, Skip: 1, Limit: 1
    Query : db.books.find().sort({ _id: 1 }).skip(1).limit(1)
    Réponse : "1984" (George Orwell, 1949)

### Q6 — Document à auteurs multiples

    titre: "Guide de survie en forêt"
    Oui, il a bien un champ auteurs au pluriel tableau : ["J. Dupont", "M. Martin"]

### Q7 — Champ chapitres ?
    
    Oui, même document : chapitres: ["Orientation", "Feu", "Abri"]

### Q8 — Le plus ancien

    Compass : tri { annee: 1 }, Limit: 1
    Query : db.books.find().sort({ annee: 1 }).limit(1)
    Réponse : "L'Étranger" Albert Camus, 1942

### Q9 — Le plus récent

    Compass : tri { annee: -1 }, Limit: 1
    Query : db.books.find().sort({ annee: -1 }).limit(1)
    Réponse : Guide de survie en forêt, 2020

### Q10 — Le champ unique

    { illustrations: { $exists: true } }
    "Guide de survie en forêt" — seul document avec le champ illustrations: true

## 1.3 — Filtrer
### Q11 — Une année précise

    { annee: 2018 }
    "Cuisine du monde"

### Q12 — Publiés après 2000

    { annee: { $gt: 2000 } }
    3 livres : Guide de survie en forêt (2020), Cuisine du monde (2018), Manuel de jardinage (2015)

### Q13 — Publiés avant 1950

    { annee: { $lt: 1950 } }
    3 livres : Le Petit Prince (1943), 1984 (1949), L'Étranger (1942)

### Q14 — Filtre sur un tableau

    { chapitres: "Feu" }
    "Guide de survie en forêt" (contient "Feu" dans son tableau chapitres)

### Q15 — Par nom d'auteur exact

    { auteur: "Isaac Asimov" }
    "Fondation" (1951)

## 1.4 — Modifier
### Q16 — Ajouter un champ
    
    db.books.updateOne({ titre: "1984" }, { $set: { note: 5 } })

### Q17 — Vérifier l'ajout
    
    Oui

### Q18 — Ajouter un document

    { "titre": "Les Misérables", "auteur": "Victor Hugo", "annee": 1862 }
    db.books.insertOne({ titre: "Les Misérables", auteur: "Victor Hugo", annee: 1862 })

### Q19 — Vérifier le compteur

    Oui j'ai bien maintenant 9 documents

### Q20 — Supprimer

    db.books.deleteOne({ titre: "Les Misérables" })
    Et maintenant j'ai bien 8 documents
