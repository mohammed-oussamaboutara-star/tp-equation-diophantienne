# tp-equation-diophantienne
Programme Python pour résoudre une équation diophantienne avec l’algorithme d’Euclide étendu
# Programme : Résolution d'une équation diophantienne a*x + b*y = c
# Auteur : [Ton Nom]
# Date : [Date d’aujourd’hui]
# Objectif : Calculer les solutions d'une équation diophantienne à l'aide de l'algorithme d'Euclide étendu

def euclide_etendu(a, b):
    """Retourne le PGCD de (a,b) et les coefficients de Bézout (x, y)"""
    if b == 0:
        return a, 1, 0
    else:
        d, x1, y1 = euclide_etendu(b, a % b)
        x = y1
        y = x1 - (a // b) * y1
        return d, x, y


# --- Interaction avec l'utilisateur ---
print("=== Résolution de l'équation diophantienne a*x + b*y = c ===")

a = int(input("Entrez la valeur de a : "))
b = int(input("Entrez la valeur de b : "))
c = int(input("Entrez la valeur de c : "))

# --- Calcul du PGCD et coefficients ---
d, x, y = euclide_etendu(a, b)

print(f"\nLe PGCD de ({a}, {b}) est : {d}")

if c % d != 0:
    print(f"Aucune solution entière car {d} ne divise pas {c}.")
else:
    # Trouver une solution particulière
    x0 = x * (c // d)
    y0 = y * (c // d)
    print(f"Une solution particulière est : x = {x0}, y = {y0}")
    print(f"La solution générale est :")
    print(f"x = {x0} + {(b // d)} * t")
    print(f"y = {y0} - {(a // d)} * t")
