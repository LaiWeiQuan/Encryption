"""
Key for the Encryption
"""
keyMatrix = [
    [13,14,20],
    [27,11,2],
    [3,7,21]
]

"""
Key for the Decryption
Inverse of the key
"""
DecryptMatrix = [
    [(-217/1913), (154/1913), (192/1913)],
    [(561/1913), (-213/1913), (-514/1913)],
    [(-156/1913), (49/1913), (235/1913)]
]

"""
Each char maps onto a number
Each number maps onto a char
"""
alphaDict = {
    'a':0,0:'a',
    'b':1,1:'b',
    'c':2,2:'c',
    'd':3,3:'d',
    'e':4,4:'e',
    'f':5,5:'f',
    'g':6,6:'g',
    'h':7,7:'h',
    'i':8,8:'i',
    'j':9,9:'j',
    'k':10,10:'k',
    'l':11,11:'l',
    'm':12,12:'m',
    'n':13,13:'n',
    'o':14,14:'o',
    'p':15,15:'p',
    'q':16,16:'q',
    'r':17,17:'r',
    's':18,18:'s',
    't':19,19:'t',
    'u':20,20:'u',
    'v':21,21:'v',
    'w':22,22:'w',
    'x':23,23:'x',
    'y':24,24:'y',
    'z':25,25:'z',
    ' ':26,26:' '
    
 }

"""
modulo of fraction calculator
"""
def moduloDecrypt():
    #Largest Common Denominator
    LCD = -1913
    ModuloMatrix = [
        [0,0,0],
        [0,0,0],
        [0,0,0]
    ]
    n = 0
    while True:
        if (n*LCD) % 27 == 1:
            break
        n+=1
    for i in range(3):
        for j in range(3):
            ModuloMatrix[i][j] = (DecryptMatrix[i][j]*LCD*n)
    # print(n)
    return ModuloMatrix
    
    

"""
Encryption
"""
def encrypt(messageVector, n, cipherMatrix):
    for i in range(3):
        for j in range(n+1):
            for x in range(3):
                cipherMatrix[i][j] += (keyMatrix[i][x] * messageVector[x][j])
            cipherMatrix[i][j] = cipherMatrix[i][j] % 27 
    # print("Cipher Text:")
    # for i in cipherMatrix:
    #     print(i)
    return cipherMatrix
    

"""
Decryption
"""
def decrypt(messageVector, n, cipherMatrix):
    modulo = moduloDecrypt()
    # print("After modulo:")
    # for i in modulo:
    #     print(i)
    for i in range(3):
        for j in range(n+1):
            cipherMatrix[i][j] = 0
            for x in range(3):
                cipherMatrix[i][j] += (modulo[i][x] *
                                       messageVector[x][j])
            cipherMatrix[i][j] = cipherMatrix[i][j] % 27  
    return cipherMatrix        

"""
Prints out the result of the matrix multiplication of the key or the key inverse
"""
def HillCipher(message, procedure):
    length = len(message)
    n = (length-1)//3
    messageVector = [[26]*(n+1) for i in range(3)]
    cipherMatrix = [[0]*(n+1) for i in range(3)]
    # print(messageVector)
    j = 0
    for i in range(length):
        if i % 3 == 0 and i != 0:
            j+=1
        messageVector[i%3][j] = alphaDict[message[i]]
        
    # print("Message:")
    # for i in messageVector:
    #     print(i)
    cipherMatrix = procedure(messageVector, n, cipherMatrix)
    Text = ""
    for j in range(0,n+1):
        for i in range(3):
            Text+=alphaDict[cipherMatrix[i][j]]
    return Text
 
def main():
    # Enter any word
    message = "linear algebra is easy"
    encryptWord = HillCipher(message.lower(), encrypt)
    print(f"After Encryption: {encryptWord}")
    decryptWord = HillCipher(encryptWord, decrypt)
    print(f"After Decryption: {decryptWord}")


if __name__ == "__main__":
    main()
