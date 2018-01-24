from operator import itemgetter


def unique_list(l): #in tabe ngarm haye ezafi ra hazf mikonad
    ulist = []
    [ulist.append(x) for x in l if x not in ulist]
    return ulist



def levenshtein(s1, s2): #in tabe faseleye levenshtein beine do reshte ra hesab mikonad
    if len(s1) < len(s2):
        return levenshtein(s2, s1)
    if len(s2) == 0:
        return len(s1)
    previous_row = range(len(s2) + 1)
    for i, c1 in enumerate(s1):
        current_row = [i + 1]
        for j, c2 in enumerate(s2):
            insertions = previous_row[j + 1] + 1 # j+1 instead of j since previous_row and current_row are one character longer
            deletions = current_row[j] + 1       # than s2
            substitutions = previous_row[j] + (c1 != c2)
            current_row.append(min(insertions, deletions, substitutions))
        previous_row = current_row
    return previous_row[-1]
#########################################################################################################
#meghdardehihayeavaliye
n=6
strings=""
output = {}
dictlist=[]
sentencefinal=[]
dictlistngram=[]
searchlistngram=[]
levenghabli=100
levenjadid=100
finalSring=""
stringghabli=""

sentenceinputforsearch=input("Enter a sentence to search :") #daryafte jomle baraye por kardane jaye khali ash
#" planes month"
count=0
N=87
q=0
z=1
lines=[]
splitlist=[]
f= open("minitrain.txt","r")
#print (len(open("minitrain.txt").readlines()))
for ck in range(N):
    line=f.readline()
    lines.append(line)
#sentenceinputforsearch=" On Wednesday , he demands for a new election or recount ."
sentenceinputforsearch=sentenceinputforsearch.split(' ')  #token token kardane reshte voroodi
for csl in range(len(sentenceinputforsearch)-n+1):
    splitsentense = ' '.join(sentenceinputforsearch[csl:csl+n])
    searchlistngram.append(splitsentense)    #listi az token ha
for search in searchlistngram:
    del sentencefinal[:]
    sentencefinal.append(["0",1000])
    sentencetest=str(search)
    for mishi in lines: #daryafte jomle haye daroone minifile & moghayese ba jomla woroodi
        input1=mishi
        input1 = input1.split(' ')
       # print(input1)
        for countngram in range(len(input1)-n+1): #ngram kardan
             g = ' '.join(input1[countngram:countngram+n])
             splitlist.append(g)
       # print(splitlist)
        for m in splitlist:
            dictlistngram.append([str(m),levenshtein(sentencetest,str(m))])
            if levenshtein(sentencetest,str(m))<levenjadid:
                levenjadid=levenshtein(sentencetest,str(m))
        dictlistngram.sort(key=itemgetter(1))
        #for miyo in dictlistngram:
         #   print(miyo)
        if count==0:
            del sentencefinal[:]
            sentencefinal.append(dictlistngram[0])
        if count!=0:
              if levenghabli>levenjadid: #moghayese faseleye levenshtaine yek ngram
                del sentencefinal[:]
                levenghabli=levenjadid
                sentencefinal.append(dictlistngram[0])
        count=count+1
      #  print(sentencefinal,"Liiiiiiiiiiiiiiiiiiiiiine",count)
        strings=str(sentencefinal[0][0])
      #  print(strings)
        del splitlist[:]
        del dictlistngram[:]
    #############################################################################################################
    if stringghabli!=strings:
        finalSring=finalSring+' '+strings
    stringghabli=strings
    levenghabli=100
    levenjadid=100
#a="calvin klein design dress calvin klein"
finalSring=' '.join(unique_list(finalSring.split()))
print(finalSring)   #chap jomleei ke jaye khaliye an por shode
