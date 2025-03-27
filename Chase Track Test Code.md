from random import randint

p_mods = [3,3,4,4,4,5,5,5,5,6,6]

track_lenth = 20
rrdw = [[1,2,2],[1,2,3],[2,3,4]]
rrdl = [[0,0,0],[-1,-1,-1],[-2,-2,-3]]
rrdc = [[12,16,18],[10,16,18],[14,17,20]]

def pturn(pos,spos):
    i = 0#randint(0,2)
    j = 2#randint(0,2)
    roll = randint(1,20)
    score = roll + 5
    if score >= rrdc[i][j]:
        pos += rrdw[i][j]
    else:
        spos -= rrdl[i][j]
    return pos, spos

def sturn(spos):
    roll = randint(1,20)
    if roll <= 5:
        spos += 1
    elif roll <= 13:
        spos += 2
    elif roll <= 18:
        spos += 3
    else:
        spos += 4
    return spos

wins = 0 
losses = 0
turns = 0


for k in range(10000):
    pos = 10 
    spos = 1 
    while True:
        i = randint(0,2)
        j = randint(0,2)
        roll = randint(1,20)
        score = roll + 5
        pos, spos = pturn(pos,spos)
        turns += 1
        if spos >= pos:
            losses += 1 
            break
        if pos >= 21:
            wins += 1
            break
        spos = sturn(spos)
        if spos >= pos:
            losses += 1 
            break
        pos, spos = pturn(pos,spos)
        turns += 1
        if spos >= pos:
            losses += 1 
            break
        if pos >= 20:
            wins += 1
            break
        
print(wins,losses,turns/10000)