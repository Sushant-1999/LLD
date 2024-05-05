# SplitWise

1) Intro
    * It is an app where we can add expense and split it between friends
    * For Eg We have added 100 then we can split it with added friends. 


2) Requirement Gathering (via Understanding(using) the Flow of the Application)

    * Can add many n  friends
    * Can create n Groups
    * Can add friends to a particular group
    * Inside Group can add expenses
    * Expenses must get splitted between added friends

    * Requirements : 
        * We should be able to add Friends
        * We should be able to add/Manage group
        * We should able to add/manage friends inside a group
        * Manage expenses inside a Group / without a group
        * Split the expenses capability 
            * Equal Split 
            * Unequal Split 
            * % Wise Split 
        * Balance Sheet of each User we wanted

3) Objects Identification for Schema Design

    * Splitwise 
    * User 
    * Group
    * Expenses
    * Split 
    * BalanceSheet

4) DeepDive with Split Wise

    * When we create an Expense like LUNCH, it will be splitted equally with the friends and in UI it will be seen.
    * 

5) UML Diagram (Classes and Their Relationships)

    * Expense 
        * ExpenseId int
        * Description string 
        * Amount int 
        * User PaidByUser
        * splitType SplitType 
        * List<Expense, > Split
         
    * Split 
        * user User
        * amount double
        * Percentage int

    * User
        * UserId int
        * UserName string 
        * UserExpenseBalanceSheet(For each user there will be Balance sheet having how much to owe from friends. So every User will be having balance sheet associated with him)

    * Expense Controller 
        * CreateExpense()
        * ValidateSplitRequest()
            * EqualSplit
            * UnequalSplit
            * PercentageSplit

    * UserController (To manage multiple Users)
        * List<User, > list
        * CRUD Operations (add , remove, update, delete)


    * Group
        * GroupId int
        * GroupName string
        * List<User, > userList
        * List<Expense, > expList
        * ExpenseController


    * Group Controller 
        * List<Group,> groupList
        * CRUD Operations of Groups

    * User Expense Balance Sheet 
    
        * (Balance Sheet has list of User and corresponding Balance(getBack and OweMoney Details from his friends))
        * Map<User, Balance> FriendBalance
        * totalMyExpense double
        * TotalPayment double
        * TotalOwe double
        * TotalGetBack double
        * So as soon as expense is getting created we need to update the balance sheet as well so Controller needs to take this responsibility. 
        * So, here comes the Balance Sheet Controller  

    * Balance 
        * AmountOwe double
        * AmountGetBack double

    * Balance Sheet Controller 
        * Expense Sheet controller will call balance sheet controller to update the Balance Sheets 
        * 