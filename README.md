from itertools import product

print("Startkarte bitte eingeben")
sk = int(input())

Karten = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]

for i in range(1, 7):

    zweg = product(Karten, repeat=i)

    for x in zweg:
        y = list(x)

        z = sum(y[:-1])

        if sum(y) + sk == 17 and z not in [17, 18, 19, 20, 21]:
            print(y)