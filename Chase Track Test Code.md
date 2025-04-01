from random import randint

track_lenth = 20
rrdw = [[1,2,2],[1,2,3],[2,3,4]]
rrdl = [[0,0,0],[-1,-1,-1],[-2,-2,-3]]
rrdc = [[12,16,18],[10,16,18],[14,17,20]]

def pturn(pos,spos):
    i = 0#randint(0,2)
    j = 2#randint(0,2)
    roll = randint(1,20)
    score = roll + 5
    pos += 0
    if score >= rrdc[i][j]:
        pos += rrdw[i][j]
    else:
        spos -= rrdl[i][j]
    return pos, spos

def sturn(spos):
    roll = randint(1,20)
    check1 = True if spos < 5 else False
    check2 = True if spos < 9 else False
    spos += 0
    if roll <= 2:
        spos += 1
    elif roll <= 8:
        spos += 1
    elif roll <= 18:
        spos += 2
    else:
        spos += 3
    if check1 and spos > 4:
        roll = randint(1,3)
        DC = 4 + 4*roll
        for i in range(4):
            roll2 = randint(1,20) + 3 
            if roll2 < DC:
                spos += 1
    if check2 and spos > 8:
        roll = randint(1,3)
        DC = 4 + 4*roll
        for i in range(4):
            roll2 = randint(1,20) + 3 
            if roll2 < DC:
                spos += 1
    return spos

wins = 0 
losses = 0
turns = 0


for k in range(10000):
    pos = 9 
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
        if pos >= 21:
            wins += 1
            break
        
print(wins,losses,turns/10000)