def queens (n=8):

sols = []

def (cols, diag1, diag2, placed):

r = len(placed)

ifrn

sols.append(placed[:])

return

for c in range(n):

if c not in cols and (rc) not in diag1 and (r + c) not in diag2:

bt(cols | {c), diag1 | {rc), diag2 | {r+c}, placed + [c])

bt(set(), set(), set(), [])

return sols

sols = queens()

print(f"Total: {len(sols)}\n")

for i, s in enumerate (sols[:2], 1):

print(f"solution {i}: {s}")

forr in range(8):

print('.join('q' if c == s[r] else'.' for c in range(8)))

print()
