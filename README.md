# Оголошення предикатів
def descendant(name1, name2):
    # Логіка визначення відношення між нащадком і предком
    pass
def male(name):
    # Логіка визначення чоловічої статі
    pass
def female(name):
    # Логіка визначення жіночої статі
    pass
# Додавання фактів
descendant('Maria', 'Ivan')
descendant('Ivan', 'Petro')
male('Ivan')
female('Maria')
# Оголошення правил
def father(name1, name2):
    if descendant(name2, name1) and male(name1):
        return True
    return False
def mother(name1, name2):
    if descendant(name2, name1) and female(name1):
        return True
    return False
def brother(name1, name2):
    if father(name1, name1) and father(name1, name2) and name1 != name2:
        return True
    return False

def sister(name1, name2):
    if mother(name1, name1) and mother(name1, name2) and name1 != name2:
        return True
    return False
def grandmother(name1, name2):
    if descendant(name2, name1) and female(name1):
        return True
    return False
def grandfather(name1, name2):
    if descendant(name2, name1) and male(name1):
        return True
    return False
def uncle(name1, name2):
    if brother(name1, name1) and male(name1):
        return True
    return False

def aunt(name1, name2):
    if sister(name1, name1) and female(name1):
        return True
    return False
# Заповнення списку імен
names = ['Maria', 'Ivan', 'Petro', 'Pavlina']
# Знаходження всіх пар рідних братів (сестер)
siblings = []
for name1 in names:
    for name2 in names:
        if name1 != name2 and brother(name1, name2):
            siblings.append((name1, name2))
print("Пари рідних братів (сестер):", siblings)
