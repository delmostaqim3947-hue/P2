# Préparation : Jeu de données
notes = [12, 9, 15, 8, 17, 13, 19, 10]

# Étape 1 : Comprendre la moyenne
if not notes:
    print("Aucune note à traiter.")
    exit()

total = 0
nb_notes = len(notes)
for note in notes:
    total += note # total = total + note

moyenne_initiale = total / nb_notes
print(f"Moyenne initiale : {moyenne_initiale:.2f}")

# Étape 2 : Ajouter +1 à chaque note (Bonus pédagogique, max 20)
# Utilisation d'une list comprehension
notes_bonus = [min(note + 1, 20) for note in notes]
print("Notes après bonus :", notes_bonus)

# Étape 3 : Filtrer les notes au-dessus d'un seuil
seuil = 12
notes_valides = [note for note in notes if note >= seuil]
print(f"Notes >= {seuil} : {notes_valides}")

# Étape 4 : Générer un petit rapport texte
moyenne_bonus = sum(notes_bonus) / len(notes_bonus)

lignes = []
lignes.append("=== Rapport des notes ===")
lignes.append(f"Nombre d'étudiants : {nb_notes}")
lignes.append(f"Notes originales : {notes}")
lignes.append(f"Notes après bonus : {notes_bonus}")
lignes.append(f"Moyenne initiale : {moyenne_initiale:.2f}")
lignes.append(f"Moyenne après bonus : {moyenne_bonus:.2f}")
lignes.append(f"Notes >= {seuil} : {notes_valides} (soit {len(notes_valides)} étudiants)")
lignes.append("Détails par étudiant :")

# Ajouter une ligne détaillée pour chaque étudiant
for index, note in enumerate(notes, start=1):
    bonus = notes_bonus[index - 1]
    lignes.append(f" Étudiant {index:02d} - note {note:>5.2f} -> bonus {bonus:>5.2f}")

# Fusionner et afficher
rapport = "\n".join(lignes)
print(rapport)

# Optionnel : Sauvegarder dans un fichier
with open("rapport_notes.txt", "w", encoding="utf-8") as f:
    f.write(rapport
