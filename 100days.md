
## Day 2 of 100 of days of code challenge

This is part of a small game I've been working on the side for a while. 
It's a text RPG, and really it's just something to keep my mind busy with code.
I've really been busy with other school aspects, but I've decided to redo a bit of the code inside.
It... sort of functions, not all of it does however. You can lose or win the battle vesus the dragon, but not al implementations are 
in it yet, such as you technically have infinite mana, and for some reason a shield is randomly added somehow.
If you wanted to play it, just pretend you have to maintain mana for attacks ;)
I find the balance is rather well number wise, however. It's a side-project anyway.

```markdown

import random, math
wizard = {'Health':350, 'Mana':500, 'Shield':0, 'Defense':50}

def boss_attack(power,defn,status,shield):
    
    if power == 1:
        dmg = random.randint(100,200)
    elif power == 0:
        dmg = random.randint(25,75)
    if random.randint(20,90) > defn:
        dmg = dmg*1.5
    if status == 1:
        dmg = dmg * 0.75
    if status == 1:
        if random.randint(1,100) > 50:
            print("Boss was frozen and didn't attack! Huzzah!")
            dmg = 0
    if shield > 0:
        raw_dmg = int(dmg)
        dmg -= shield
        shield -= raw_dmg        
        print('Your shield negated some damage, but it is weaker now.')
        if dmg < 0:
            dmg = 0
            print('Your shield complete negated the attack! You have %f of a charge left.'%shield)
    print('The dragon did %.2f damage to you!'%dmg)
    
    return dmg

def fireball():
    attk = random.randint(50,150)
    if random.randint(1,50) > 25:
        attk = attk*2
    return attk
def icebolt():
    attk = random.randint(85,120)
    if random.randint(1,50) > 25:
        attk = attk*1.75
    return attk


def victory():
    global battle
    print('You have defeated the dragon! Nicely done! Now, enjoy the satisfaction.')
    battle = False
    return battle
def defeat():
    global battle
    print('Much to your dismay, your sinched corpse is now being consumed by the dragon... but you may simply re-run the game ;p')
    battle = False
    return battle

def combat():
    global wizard
    battle = True
    bossHP = 5000
    manaPots = 10
    hpPots = 5
    status = 0
    pHP = wizard['Health']
    pMP = wizard['Mana']
    pSLD = wizard['Shield']
    pDEF = wizard['Defense']
    
    while battle:
        move = input('Enter 1 for fireball, 2 for icebolt, 3 to shield, 4 to use'+
            ' a mana potion, or 5 for a health potion.'+'\n' + 'Each move uses a turn!\n'+
                    'You have %d health potions and %d mana potions left.'%(hpPots,manaPots)+
                     'Your HP is: %.2f and mana is: %d'%(pHP,pMP))
        if move == '1':
            pMP -= 100
            fireball()
            bossHP -= fireball()
            print('Your fireball did %.2f damage!'%fireball())
            damage = boss_attack(0,50,0,pSLD)
            pHP -= damage 
            pSLD = pSLD - (pSLD - damage)
            if pSLD < 0:
                pSLD = 0
            print('You have %.2f HP left!'%pHP)
            if bossHP <= 0:
                victory()
                battle = False
            if pHP <=0:
                defeat()
                battle = False
            
       
            
        if move == '2':
            pMP -= 75
            icebolt()
            bossHP -= icebolt()
            print('Your icebolt did %.2f damage!'%icebolt())
            if random.randint(1,10) > 3:
                status = 1
                print('Dragon looks rather chilly and sluggish after that hit...')
                pHP -= boss_attack(0,50,1,pSLD)
                print('You have %.2f HP left!'%pHP)
                
            else:
                 damage = boss_attack(0,50,0,pSLD)
                 pHP -= damage 
                 pSLD = pSLD - (pSLD - damage)
                 if pSLD < 0:
                     pSLD = 0
                 print('You have %.2f HP left!'%pHP)

            if pHP <=0:
                defeat()
                battle = False            
                            
        if move == '3':
            pMP -= 100
            pSLD += 125
            damage = boss_attack(0,50,0,pSLD)
            pHP -= damage 
            pSLD = pSLD - (pSLD - damage)
            if pSLD < 0:
                pSLD = 0
            
            print('You have %.2f HP left!'%pHP)
            if pHP <=0:
                defeat()
                battle = False
        if move == '4':
            manaPots -= 1
            pMP += 100
            damage = boss_attack(0,50,0,pSLD)
            pHP -= damage 
            pSLD = pSLD - (pSLD - damage)
            if pSLD < 0:
                pSLD = 0
            print('You have %.2f HP left!'%pHP)
            if pHP <=0:
                defeat()
                battle = False
        if move == '5':
            if hpPots == 0:
                print("You don't have anymore health potions!")
                damage = boss_attack(0,50,0,pSLD)
                pHP -= damage 
                pSLD = pSLD - (pSLD - damage)
                if pSLD < 0:
                    pSLD = 0
                print('You have %.2f HP left!'%pHP)
                if pHP <=0:
                    defeat()
                    battle = False
            if hpPots != 0:
                hpPots -=1
                pHP += 150
                damage = boss_attack(0,50,0,pSLD)
                pHP -= damage 
                pSLD = pSLD - (pSLD - damage)
                if pSLD < 0:
                    pSLD = 0
                print('You have %.2f HP left!'%pHP)
                if pHP <=0:
                    defeat()
                    battle = False
```

I find it's a good challenge, either way. There's a bit I don't know, and if I learn how to fix/do the stuff, the all the better I become!

        


    














## Day 1 of 100 days of code challenge

This is not only day 1 of the 100 days of code challenge, but my first day of using Github and first blog post!

### Math challenge

This is a coding challenge, calling for taking two number arguements - a/b - and adding all numbers inbetween them including themselves. If a = b, then simply return either or; the function should as well account for negative numbers. I did this in Python:

```markdown
def sum_nums(a , b):
    if a == b:
        return a
    if a < b:
         while a != b:   
            for x in range(a+1,b+1):
                a+=x
            return a
    if a > b:
        while b != a:
            for x in range(b+1,a+1):
                b+=x
            return b
```

I ran the code with both positive and negative integers, and it seems to compute correctly. I am decently sure this may be cleaned up a bit, and the syntax seems a bit barbaric, but it works!
Now, to figure out how to do multiple days and become familiar with Github...

Until next time!
