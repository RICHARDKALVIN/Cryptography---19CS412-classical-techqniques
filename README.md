# Cryptography---19CS412-classical-techqniques


# Caeser Cipher
Caeser Cipher using with different key values

# AIM:

To develop a simple C program to implement Caeser Cipher.

## DESIGN STEPS:

### Step 1:

Design of Caeser Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```
A python program to illustrate Caesar Cipher Technique
def encrypt(text,s):
    result = ""
# traverse text
for i in range(len(text)):
    char = text[i]
# Encrypt uppercase characters
if (char.isupper()):
    result += chr((ord(char) + s-65) % 26 + 65)
# Encrypt lowercase characters
else:
    result += chr((ord(char) + s - 97) % 26 + 97)
return result
check the above functiontext = "Richard"
s = 3
print ("Text : " + text)
print ("Shift : " + str(s))
print ("Cipher: " + encrypt(text,s))
def decrypt():
#enter your encrypted message(string) below
    encrypted_message = input("Enter the message i.e to be decrypted: ").strip()
    letters="abcdefghijklmnopqrstuvwxyz"
#enter the key value to decrypt
    k = int(input("Enter the key to decrypt: "))
    decrypted_message = ""
    for ch in encrypted_message:
       if ch in letters:
            position = letters.find(ch)
    new_pos = (position - k) % 26
    new_char = letters[new_pos]
    decrypted_message += new_char
        else:
           decrypted_message += ch
           print("Your decrypted message is:\n")
           print(decrypted_message)
decrypt()
```

## OUTPUT:

ENCRYPTION:
Text : Richard
Shift: 3
Encrypted Cipher: ulfkdug
DECRYPTION:
Enter the message i.e to be decrypted: ulfkdug
Enter the key to decrypt: 3
Your decrypted message is: Richard

## RESULT:
The program is executed successfully

---------------------------------

# PlayFair Cipher
Playfair Cipher using with different key values

# AIM:

To develop a simple C program to implement PlayFair Cipher.

## DESIGN STEPS:

### Step 1:

Design of PlayFair Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```
# Python program to implement Playfair Cipher
# Function to convert the string to lowercase
def toLowerCase(text):
return text.lower()
# Function to remove all spaces in a string
def removeSpaces(text):
newText = ""
for i in text:
if i == " ":
continueelse:
newText = newText + i
return newText
# Function to group 2 elements of a string
# as a list element
def Diagraph(text):
Diagraph = []
group = 0
for i in range(2, len(text), 2):
Diagraph.append(text[group:i])
group = i
Diagraph.append(text[group:])
return Diagraph
# Function to fill a letter in a string element
# If 2 letters in the same string matches
def FillerLetter(text):
k = len(text)
if k % 2 == 0:
for i in range(0, k, 2):
if text[i] == text[i+1]:
new_word = text[0:i+1] + str('x') + text[i+1:]
new_word = FillerLetter(new_word)
break
else:new_word = text
else:
for i in range(0, k-1, 2):
if text[i] == text[i+1]:
new_word = text[0:i+1] + str('x') + text[i+1:]
new_word = FillerLetter(new_word)
break
else:
new_word = text
return new_word
list1 = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i', 'k', 'l', 'm',
'n', 'o', 'p', 'q', 'r', 's', 't', 'u', 'v', 'w', 'x', 'y', 'z']
# Function to generate the 5x5 key square matrix
def generateKeyTable(word, list1):
key_letters = []
for i in word:
if i not in key_letters:
key_letters.append(i)
compElements = []
for i in key_letters:
if i not in compElements:
compElements.append(i)
for i in list1:
if i not in compElements:
compElements.append(i)matrix = []
while compElements != []:
matrix.append(compElements[:5])
compElements = compElements[5:]
return matrix
def search(mat, element):
for i in range(5):
for j in range(5):
if(mat[i][j] == element):
return i, j
def encrypt_RowRule(matr, e1r, e1c, e2r, e2c):
char1 = ''
if e1c == 4:
char1 = matr[e1r][0]
else:
char1 = matr[e1r][e1c+1]
char2 = ''
if e2c == 4:
char2 = matr[e2r][0]
else:
char2 = matr[e2r][e2c+1]
return char1, char2def encrypt_ColumnRule(matr, e1r, e1c, e2r, e2c):
char1 = ''
if e1r == 4:
char1 = matr[0][e1c]
else:
char1 = matr[e1r+1][e1c]
char2 = ''
if e2r == 4:
char2 = matr[0][e2c]
else:
char2 = matr[e2r+1][e2c]
return char1, char2
def encrypt_RectangleRule(matr, e1r, e1c, e2r, e2c):
char1 = ''
char1 = matr[e1r][e2c]
char2 = ''
char2 = matr[e2r][e1c]
return char1, char2
def encryptByPlayfairCipher(Matrix, plainList):
CipherText = []
for i in range(0, len(plainList)):
c1 = 0c2 = 0
ele1_x, ele1_y = search(Matrix, plainList[i][0])
ele2_x, ele2_y = search(Matrix, plainList[i][1])
if ele1_x == ele2_x:
c1, c2 = encrypt_RowRule(Matrix, ele1_x, ele1_y, ele2_x, ele2_y)
# Get 2 letter cipherText
elif ele1_y == ele2_y:
c1, c2 = encrypt_ColumnRule(Matrix, ele1_x, ele1_y, ele2_x, ele2_y)
else:
c1, c2 = encrypt_RectangleRule(
Matrix, ele1_x, ele1_y, ele2_x, ele2_y)
cipher = c1 + c2
CipherText.append(cipher)
return CipherText
1. decrypted_text = playfair_cipher(ciphertext, key, 'decrypt')
2. print(decrypted_text)# (Note: 'x' is added as padding)
text_Plain = 'Richard'
text_Plain = removeSpaces(toLowerCase(text_Plain))
PlainTextList = Diagraph(FillerLetter(text_Plain))
if len(PlainTextList[-1]) != 2:
PlainTextList[-1] = PlainTextList[-1]+'z'
key = "key"
print("Key text:", key)
key = toLowerCase(key)
Matrix = generateKeyTable(key, list1)print("Plain Text:", text_Plain)
CipherList = encryptByPlayfairCipher(Matrix, PlainTextList)
CipherText = ""
for i in CipherList:
CipherText += i
print("CipherText:", CipherText)
```
## OUTPUT:
ENCRYPTION:
Key text: kal
Plain text: Richard
Cipher text: qm hp ew eq
DECRYPTION:
Enter the message i.e to be decrypted: qm hp ew eq
Enter the key to decrypt: kal
Your decrypted message is: Richard

## RESULT:
The program is executed successfully


---------------------------

# Hill Cipher
Hill Cipher using with different key values

# AIM:

To develop a simple C program to implement Hill Cipher.

## DESIGN STEPS:

### Step 1:

Design of Hill Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```
# Python3 code to implement Hill Cipher
keyMatrix = [[0] * 3 for i in range(3)]
# Generate vector for the message
messageVector = [[0] for i in range(3)]
# Generate vector for the cipher
cipherMatrix = [[0] for i in range(3)]
# Following function generates the
# key matrix for the key string
def getKeyMatrix(key):
k = 0
for i in range(3):
for j in range(3):
keyMatrix[i][j] = ord(key[k]) % 65
k += 1# Following function encrypts the message
def encrypt(messageVector):
for i in range(3):
for j in range(1):
cipherMatrix[i][j] = 0
for x in range(3):
cipherMatrix[i][j] += (keyMatrix[i][x] *
messageVector[x][j])
cipherMatrix[i][j] = cipherMatrix[i][j] % 26
def HillCipher(message, key):
# Get key matrix from the key string
getKeyMatrix(key)
# Generate vector for the message
for i in range(3):
messageVector[i][0] = ord(message[i]) % 65
# Following function generates
# the encrypted vector
encrypt(messageVector)
def main():
message = input("enter a plaintext to encrypt")
K = np.matrix([[3, 3], [2, 5]])
Kinv = matrix_mod_inv(K, len(alphabet))
decrypted_message = decrypt(encrypted_message, Kinv)
print("Original message: " + message)
print("Decrypted message: " + decrypted_message)
# Generate the encrypted text# from the encrypted vector
CipherText = []
for i in range(3):
CipherText.append(chr(cipherMatrix[i][0] + 65))
# Finally print the ciphertext
print("Ciphertext: ", "".join(CipherText))
# Driver Code
def main():
# Get the message to
# be encrypted
message = "ERA"
# Get the key
key = "ABBCCDDEE"
HillCipher(message, key)
if __name__ == "__main__":
main()
```
## OUTPUT:
ENCRYPTION:
Ciphertext: IOR
Key: ABBCCDDEE
DECRYPTION:
Enter the message i.e to be decrypted: IOR
Enter the key to decrypt: ABBCCDDEE
Your decrypted message is: ERA

## RESULT:
The program is executed successfully

-------------------------------------------------

# Vigenere Cipher
Vigenere Cipher using with different key values

# AIM:

To develop a simple C program to implement Vigenere Cipher.

## DESIGN STEPS:

### Step 1:

Design of Vigenere Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```
# Python code to implement
# Vigenere Cipher
# This function generates the
# key in a cyclic manner until
# it's length isn't equal to
# the length of original text
def generateKey(string, key):
key = list(key)
if len(string) == len(key):
return(key)
else:
for i in range(len(string) -
len(key)):
key.append(key[i % len(key)])
return("" . join(key))
# This function returns the# encrypted text generated
# with the help of the key
def cipherText(string, key):
cipher_text = []
for i in range(len(string)):
x = (ord(string[i]) +
ord(key[i])) % 26
x += ord('A')
cipher_text.append(chr(x))
return("" . join(cipher_text))
# This function decrypts the
# encrypted text and returns
# the original text
def originalText(cipher_text, key):
orig_text = []
for i in range(len(cipher_text)):
x = (ord(cipher_text[i]) -
ord(key[i]) + 26) % 26
x += ord('A')
orig_text.append(chr(x))
return("" . join(orig_text))
# Driver code
if __name__ == "__main__":
string = "richard"
keyword = "acd"
key = generateKey(string, keyword)
cipher_text = cipherText(string,key)
print("Ciphertext :", cipher_text)
print("Original/Decrypted Text :",
"RICHARD"
"acd"originalText(cipher_text, key))
```

## OUTPUT:
Plain Text :richard
KEY:acd
Ciphertext: skihade
DECRYPTION:
Ciphertext: skihade
Original/Decrypted Text: richard


## RESULT:
The program is executed successfully

-----------------------------------------------------------------------

# Rail Fence Cipher
Rail Fence Cipher using with different key values

# AIM:

To develop a simple C program to implement Rail Fence Cipher.

## DESIGN STEPS:

### Step 1:

Design of Rail Fence Cipher algorithnm 

### Step 2:

Implementation using C or pyhton code

### Step 3:

Testing algorithm with different key values. 

## PROGRAM:
```
# function to encrypt a message
def encryptRailFence(text, key):
# create the matrix to cipher
# plain text key = rows ,
# length(text) = columns
# filling the rail matrix
# to distinguish filled
# spaces from blank ones
rail = [['\n' for i in range(len(text))]
for j in range(key)]
# to find the direction
dir_down = False
row, col = 0, 0for i in range(len(text)):
# check the direction of flow
# reverse the direction if we've just
# filled the top or bottom rail
if (row == 0) or (row == key - 1):
dir_down = not dir_down
# fill the corresponding alphabet
rail[row][col] = text[i]
col += 1
# find the next row using
# direction flag
if dir_down:
row += 1
else:
row -= 1
# now we can construct the cipher
# using the rail matrix
result = []
for i in range(key):
for j in range(len(text)):
if rail[i][j] != '\n':
result.append(rail[i][j])
return("" . join(result))
# This function receives cipher-text
# and key and returns the original
# text after decryption
def decryptRailFence(cipher, key):# create the matrix to cipher
# plain text key = rows ,
# length(text) = columns
# filling the rail matrix to
# distinguish filled spaces
# from blank ones
rail = [['\n' for i in range(len(cipher))]
for j in range(key)]
# to find the direction
dir_down = None
row, col = 0, 0
# mark the places with '*'
for i in range(len(cipher)):
if row == 0:
dir_down = True
if row == key - 1:
dir_down = False
# place the marker
rail[row][col] = '*'
col += 1
# find the next row
# using direction flag
if dir_down:
row += 1
else:
row -= 1# now we can construct the
# fill the rail matrix
index = 0
for i in range(key):
for j in range(len(cipher)):
if ((rail[i][j] == '*') and
(index < len(cipher))):
rail[i][j] = cipher[index]
index += 1
# now read the matrix in
# zig-zag manner to construct
# the resultant text
result = []
row, col = 0, 0
for i in range(len(cipher)):
# check the direction of flow
if row == 0:
dir_down = True
if row == key-1:
dir_down = False
# place the marker
if (rail[row][col] != '*'):
result.append(rail[row][col])
col += 1
# find the next row using
# direction flagif dir_down:
row += 1
else:
row -= 1
return("".join(result))
if __name__ == "__main__":
print(encryptRailFence("Shyam", 2))
print(encryptRailFence("music", 3))
print(encryptRailFence("driving", 3))
# Now decryption of the
# same cipher-text
print(decryptRailFence("mcuis", 3))
print(decryptRailFence("symha", 2))
print(decryptRailFence("dirvnig", 3))
```

## OUTPUT:
ENCRYPTION:
Symha
Sbc hdiar
DECRYPTION:
Sbc hdiar
shyam
Richard

## RESULT:
The program is executed successfully
