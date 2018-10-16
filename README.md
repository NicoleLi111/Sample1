# Sample1

#1a) making expenses records with format siglespace
records=[]
with open('C:/Users/16268/Desktop/Intro to Python/Homework/HW2/expenses.txt', 'rt',
          encoding = 'utf-8') as fin:
    for line in fin:
        line = line[:-1]
        records.append(line)
    for line in records:
        print(line)

#1b) making list of lists
    print('\n')
records2=[]
with open('C:/Users/16268/Desktop/Intro to Python/Homework/HW2/expenses.txt', 'rt',
          encoding = 'utf-8') as fin:
    for line in fin:
        line=line[:-1]
        columns= line.split(':')
        records2.append(columns)
    for row in records2:
        print(row)
#1c) r2_copy is not ascending order by dollar amount
    print('\n')
    r2_copy=records2.copy()
    r2_copy.sort()
    for row in r2_copy:
        print(row)
#1d)separating header and the numbers
    print('\n')
    header=records2[0].copy()
    data=records2[1:].copy()
    print(header)
    for d in data:
        print(d)
#1e)turning str in list of list to float
    print('\n')
    print(header)
    for d in data:
        d[0]=float(d[0])
        print(d)
#1f)sorting the floats 
    print('\n')
    data.sort()
    print(header)
    for d in data:
        print(d)

#1g) creating sets
    print('\n')
    categories=set()
    for x in data:
        expense= x[1]
        categories.add(expense)
    print('There are',len(categories),'expense categories:')
    for c in categories:
        print(c)

#1h)creating dict
    print('\n')
n2s={'Key':'Value','01':'  Jan','02':'  Feb','03':'  Mar','04':'  Apr','05':'  May',
     '06':'  Jun','07':'  Jul','08':'  Aug','09':'  Sep','10':'  Oct','11':'  Nov','12':'  Dec'}
for x in n2s:
    y= x+'  '+ n2s[x]
    print(y)

#1i)Find total of the expenses in each category
print('\n')
def exp_report(x):
    records2 = []
    with open(x, 'rt', encoding='utf-8') as fin:
        for line in fin:
            columns = line[:-1].split(':')
            records2.append(columns)
    header = records2[0].copy()
    data = records2[1:].copy()
    for d in data:
        d[0] = float(d[0])  # change str to float
    data.sort()
    datacopy=[]
    for d in data:
        data2=[d[2],d[1],d[0],d[3]]
        datacopy.append(data2)
        datacopy.sort()

    print('{:<13}{:<10}{:<8}{:<12}'.format(header[2],header[1],header[0],header[3]))
    for d in datacopy:
        x=d[0]
        y= x[-2:]+ '-'+ n2s.get(x[-4:-2])+'-'+x[:4]
        print('{:>10}{}{:<8}{:>8.2f}{}{:<60}'.format(y,"  ",d[1],d[2],"  ",d[3]))
    total=0.0
    for d in datacopy:
        total += d[2]
    print('{:>13} total: {:>8.2f}'.format('  ',total))
    category_totals={}
    for d in datacopy:
        category= d[1]
        if category in category_totals:
            category_totals[category]+= d[2]
        else:
            category_totals[category] = d[2]
    for k in category_totals.keys():
        print('{:>13} total: {:>8.2f}'.format(k, category_totals[k]))
    
exp_report('C:/Users/16268/Desktop/Intro to Python/Homework/HW 4/expenses.txt')
    
    
        
    
    
    

    
        
        
    
    
 
        


