# Mad-Libs-styleproject.py
it reads a text file(story.txt) with placeholders wrapped in curly braces {} then it asked you to provide of each place holder  
#How it Works
The program opens story.txt and scans for placeholders like {place}, {animal}, {adjective}.
It prompts the user to enter words for each placeholder.
It replaces the placeholders with the user’s input.
The completed story is printed out
#Example
Today I went to {place}. I saw a {animal} and it was very {adjective}.
#Running
Enter a word foradjective:bad
Enter a word foranimal:tiger
Enter a word forplace:guntur
Today I went to {place}. I saw a {animal} and it was very bad.

Today I went to {place}. I saw a tiger and it was very bad.

Today I went to guntur. I saw a tiger and it was very bad.
#my coode
with open("story.txt","r")as f:
    story=f.read()
words=set()
start_of_word=-1
for i,char in enumerate(story):
    if char=="{":
        start_of_word=i
    elif char=="}" and start_of_word !=-1:
        word=story[start_of_word+1:i]
        words.add(word)
        start_of_word=-1
answers={}
for word in words:
    answer=input(f"Enter a word for{word}:")
    answers[word]=answer
for word in words:
    story=story.replace(f"{{{word}}}",answers[word])
    print(story)
