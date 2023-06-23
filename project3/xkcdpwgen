import argparse
import random

# represents a list of symbols
symbols_list = ['%','$','@','#','£','!','?','^','*',':',';','+','=']

# generates the initial blank password
password = ''

# initial list of words to be the password
init_words = []

file = open('words.txt')
all_words = file.readlines()

# sets an initial default password
for x in range(0, 4):
  rand = random.randint(1, 370105)
  init_words.append(all_words[rand].lower())
  password += all_words[rand].lower().rstrip()

# creates the command line parser
parser = argparse.ArgumentParser(description='Generate a secure, memorable password using the XKCD method')

# adds arguments to the parser
parser.add_argument('-w', '--words', type=int, default=4,
                    help='include just WORDS words in the password (default is %(default)s)')
parser.add_argument('-c', '--caps', type=int, default=0,
                    help='capitalize CAPS number of random words in the password (default is %(default)s)')
parser.add_argument('-n', '--numbers', type=int, default=0,
                    help='add NUMBERS amount of random numbers to the password (default is %(default)s)')
parser.add_argument('-s', '--symbols', type=int, default=0,
                    help='insert SYMBOLS number of random symbols in the password (default is %(default)s)')
  
args = parser.parse_args()

# sets variables as the user command line input
words = args.words
caps = args.caps
numbers = args.numbers
symbols = args.symbols

# adds a given number of words to the password
if args.words:
  password = ''
  init_words.clear()
  for x in range(0, words):
    rand = random.randint(1, 370105)
    init_words.append(all_words[rand].lower().rstrip())

# capitalizes words in the XKCD password
if args.caps:

  for x in range(0, caps):
    rand = random.randint(0, len(init_words) - 1)

    # runs until an uncapitalized word is found
    while (init_words[rand])[0].isupper():
       rand = random.randint(0, len(init_words) - 1)
       if not (init_words[rand])[0].isupper():
        break

    init_words[rand] = init_words[rand].capitalize()

# adds numbers to the XKCD password
if args.numbers:
  for x in range(0, numbers):
    # rand1 = random word in the word list
    rand1 = random.randint(0, len(init_words) - 1)
    # rand2 = random number from 0-9
    rand2 = random.randint(0, 9)
    if rand1 == 0:
      init_words.insert(0, rand2)
    else:
      init_words.insert(rand1, rand2)

if args.symbols:
  for x in range(0, symbols):
    # rand1 = random word in the word list
    rand1 = random.randint(0, len(init_words) - 1)
    # rand2 = random symbol in the list of symbols
    rand2 = random.randint(0, 12)

    if rand1 == 0:
      init_words.insert(0, symbols_list[rand2])
    else:
      init_words.insert(rand1, symbols_list[rand2])

# changes the list into the final password
for word in init_words:
  password += str(word)
  
# prints the final password
print(password)
