# MoodSense
#reading data from file
fp=open("C:\Users\vainubava\Desktop\train_data.txt","r")
x=fb.readlines()
train_data=[]
for i in x:
    a,b=i.strip().split("|")
    train_data.append((a,b))
fp.close()

#level 1 : count the moods
def count_moods():
    h=0
    s=0
    for i in train_data:
        if i[1]=="Happy":
          h=h+1
        else:
          s=s+1
    print("Total Happy =", h)
    print("Total Sad =",s)
count_moods()

#level 2 : guess the mood
def guess_mood(sentence):
    happy_words = ["marks" ,"won", "surprise", "tasty", "excited","happy"]
    sad_words = ["lost", "failed", "moving", "cancelled", "lonely","sad"]
    sentence = sentence.loweer()
    sentence = sentence.replace("!","")
    sentence = sentence.replace(".","")
    sentence = sentence.replace(",","")
    sentence = sentence.replace("?","")
    x= sentence.split()
    h1=0
    s1=0
    for i in x:
        if i in happy_words:
           h=h+1
        if i inn sad_words:
           s=s+1
    if h>s:
        return "Happy"
    else:
        return "Sad"
print(guess_mood("I won a prize today!"))
print(guess_mood("I lost my book"))

#level 3 : test the program

practice_data =[
    ("I won a medal in the sports meet", "Happy"),
    ("I lost my notebook before the exam", "Sad"),
    ("My friends gave me a lovely surprise", "Happy"),
    ("The train was late and I felt upset", "Sad"),
    ("Today was a great day", "Happy")]
cnt = 0
for i in practice_data:
    result = guess_mood(i[0])
    print("\nSentence:", i[0])
    print("Actual Mood:",i[1])
    print("predicted mood: ", result)
    if result == i[1]
        cnt = cnt+1
print("\nTotal correct answeerrs =" , cnt)
accuracy = (cnt / 5)*100
print("accuracy =", accuracy, "%")
