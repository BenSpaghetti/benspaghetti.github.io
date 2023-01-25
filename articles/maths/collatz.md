# Current Progress on Collatz

So I am currently inspecting the repeated applications of the Collatz function to positive integer pairs.

Stuff may be posted here. I can't really code so bear with me.

## 2022-11-30

Around 2/3 of integer pairs go into the eventual cycle formed by the repeated application of the Collatz mapping due to their final 1-4-2 cycle not in sync.

```py
import matplotlib.pyplot as plt
import time
from colour import Color
p = int(input("Enter p: "))
q = int(input("Enter q: "))
print(int(p), int(q), sep=", ")

def collatz(n):
    if n % 2 == 1:
        n = 3 * n + 1
    elif n % 2 == 0:
        n = n / 2
    return n

pee = [p]
kiu = [q]
k=50
i = k
plt.text(p, q, (int(p), int(q)))
plt.plot(p, q, marker='o', markerfacecolor='red', markersize=15)

while (p != 1 or q != 1) and i != 0:
    p = collatz(p)
    q = collatz(q)
    print(p, q, sep=", ")
    pee.append(p)
    kiu.append(q)
    i = i - 1
    plt.plot(p, q, marker='o', markerfacecolor=str(i/k), markersize=8)
    plt.text(p, q, (int(p), int(q)), fontsize='small')
    #time.sleep(0.5)

plt.plot(pee, kiu, color='blue', linestyle = '--', linewidth = 1)
plt.xlabel(r'$p$')
plt.ylabel(r'$q$')
plt.axis('scaled')
plt.xlim(1)
plt.ylim(1)
plt.title(r'plot of $(f(p), f(q))$, where $f(n)$ is as defined in the Collatz Conjecture')
plt.show()
```