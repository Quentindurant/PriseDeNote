
## BDD

# Trigger

```plpgsql
CREATE OR REPLACE FUNCTION set_updated_at() RETURNS trigger AS $$
BEGIN
  NEW.updated_at := now();
  RETURN NEW;
END;
$$ LANGUAGE plpgsql;
```

### Explication ligne par ligne

- **`CREATE OR REPLACE FUNCTION set_updated_at() RETURNS trigger AS $$`**
    
    - `CREATE FUNCTION` : crée une fonction dans PostgreSQL.
        
    - `OR REPLACE` : si la fonction existe déjà, elle est remplacée (utile pour la mettre à jour).
        
    - `set_updated_at()` : nom de la fonction (ici sans arguments).
        
    - `RETURNS trigger` : indique que cette fonction renvoie un trigger (obligatoire pour être utilisée dans un `CREATE TRIGGER`).
        
    - `AS $$ ... $$` : délimite le corps de la fonction (plus pratique que des quotes `'` pour du multi-lignes).
        

---

- **`BEGIN` … `END;`**
    
    - Délimite le bloc d’instructions PL/pgSQL.
        
    - Toutes les actions de la fonction doivent être entre `BEGIN` et `END`.
        

---

- **`NEW.updated_at := now();`**
    
    - `NEW` est une **pseudo-variable spéciale** dans un trigger **BEFORE**.
        
    - Elle représente la nouvelle version de la ligne (celle qui va être insérée ou mise à jour).
        
    - Ici, on modifie sa colonne `updated_at` pour la remplacer par la date/heure actuelle (`now()`).
        
    - `:=` est l’opérateur d’affectation en PL/pgSQL (équivalent du `=` en SQL classique).
        

---

- **`RETURN NEW;`**
    
    - Retourne la ligne modifiée (`NEW`) pour que PostgreSQL l’enregistre.
        
    - Si on utilisait `RETURN OLD;`, ça reviendrait à annuler la mise à jour, puisque `OLD` = la ligne avant modification.
        

---

- **`$$ LANGUAGE plpgsql;`**
    
    - `$$` marque la fin du corps de la fonction.
        
    - `LANGUAGE plpgsql` précise que la fonction est écrite en PL/pgSQL (le langage procédural de PostgreSQL, proche de PL/SQL d’Oracle).