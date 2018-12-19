# BlackJack
from itertools import product

print("Startkarte der Bank bitte eingeben (Ass ist 11 und Bildkarten sind 10:")

sk = int(input())

print("Endwert eingeben:")

ew = int(input())

Karten = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11]

liste = []

summehand = 0

for i in range(1, 7):

    zweg = product(Karten, repeat=i)

    for x in zweg:
        y = list(x)

        z = sum(y[:-1]) + sk

        if sum(y) + sk == ew and z not in [17, 18, 19, 20, 21]:

            if 1 in y:
                if sum(y[:y.index(1)]) + sk > 10:
                    liste.append(y)
            else:
                liste.append(y)

for hand in liste:

    p = 1
    for i in hand:

        if i != 10:
            i = 1 / 13

        else:
            i = 4 / 13

        p = p * i

    summehand += p

if (sk == 10 or sk == 11) and ew == 21:
    summehand = summehand - 4 / 169

    if sk == 10:
        blackjack = 1 / 13
    if sk == 11:
        blackjack = 4 / 13

    print("Wahrscheinlichkeit 21 Punkte ohne Black Jack zu erreichen beträgt:")

    print(summehand)

    print("Gerundet:")

    print(round(summehand, 4))

    print("Wahrscheinlichkeit 21 Punkte mit einem Black Jack zu erreichen beträgt:")

    print(blackjack)

    print("Gerundet:")

    print(round(blackjack,4))

else:

    print("Die Wahrscheinlichkeit beträgt:")

    print(summehand)

    print("Gerundet:")

    print(round(summehand, 4))
