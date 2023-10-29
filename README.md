

board=["-","-","-",
       "-","-","-",
       "-","-","-"]
currentPlayer ="X"
winner=None
gamerunning=True
# printing the player input
def printBoard(board):
    print(board[0]+ "  | "+ board[1]+"  |  "+board[2])
    print("___________")
    print(board[3]+ "  | "+ board[4]+"  |  "+board[5])
    print("___________")
    print(board[6]+ "  | "+ board[7]+"  |  "+board[8])
printBoard(board)
# take player input
def playerInput(board):
  inp=int(input("Enter a number (1-9): "))
  if inp >=1 and inp<=9 and board[inp-1]=="-":
    board[inp-1]=currentPlayer
  else:
    print("Player is already in the spot")
#check for win or loss
def checkHorizondal (board):
  global winner
  if board[0]==board[1]==board[2] and board[1] !="-":
    winner=board[0]
    return True 
  elif board[3]==board[4]==board[5] and board[3] !="-":
    winner=board[3]
    return True
  elif board[6]==board[7]==board[8] and board[6] !="-":
    winner=board[6]
    return True
def checkRow(board):
    global winner
    if board[0]==board[3]==board[6] and board[0] !="-":
      winner=board[0]
      return True 
    elif board[1]==board[4]==board[7] and board[1] !="-":
      winner=board[1]
      return True
    elif board[2]==board[5]==board[8] and board[6] !="-":
      winner=board[2]
      return True
def checkDiagnol(board):
  global winner 
  if board[0]==board[4]==board[8] and board[0] !="-":
    winner=board[0]
    return True
  elif board[2]==board[4]==board[6] and board[2] !="-":
    winner=board[2]
    return True
def CheckTie(board):
  if "-" not in board:
    printBoard(board)
    print("Tie")
    gameRunning=False
def checkWin():
  if checkDiagnol(board) or checkHorizondal(board) or checkRow(board):
    print(f"The winner is {winner}")
# switch player 
def switchPlayer():
  global currentPlayer
  if currentPlayer=="X":
    currentPlayer="O"
  else:
    currentPlayer="X"
# check for win or loss
while gamerunning:
  printBoard(board)
  playerInput(board)
  checkWin()
  CheckTie(board)
  switchPlayer()


