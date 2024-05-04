# Book My Show LLD

1) Object used in BookMyShow

    * User
    * Movie
    * City
    * Theatre
    * Screens
    * Seats
    * Shows
    * Booking 
    * Payment



2) Class Diagrams via Objects 

    * Movie
        * MovieId int
        * MovieName string
        * TimeDuration timestamp

    * Movie Controller
        * Map<city, ListOfMovies>
        * List<Movies, > All Movies
        
    * Theater
        * TheatreId int
        * Address string 
        * City string
        * List<Screens,> screen 
        * List<Shows, > shows

    * Screen
        * ScreenId int
        * List<Seats, > Seats

    * Shows
        * ShowId int
        * MovieDetails Movie 
        * ScreenInfo Screen
        * StartTime time
        * List<BookedSeatId, >BookedShowId

    * Seat 
        * SeatId int
        * RowId int 
        * SeatCategory Category
        

    * TheatreController 

        * Map<City, ListOfTheaters>
        * List<Theatres, >AllTheaters


    * Bookings 
        * 

2) Locking Mechanism , Concurrency to avoid Discrepancies while booking the tickets simultaneously by users 

    * Pessimistic Locking Mechanism 

        * Here whenever user try to read the tickets for booking use Lock while reading and then after updation is done then release the Lock.
        * Here multiple users can't read simultaneously. At a time only one user can read and after updation the lock will be released .


    * Optimistic Lock Mechanims

        * Multiple uses can read here but there is version matching over here

        * Optimistic Locking is the best way to take care of locking 
        * At the time of update it will check, if one seat 30 choose having v1 and now it updated version. So optimistic will check its version does it changed or not. If not changed it will lock and update and release the lock.

        * So version checking on which he is working previously that is checked if version changes then he has to undergo previous process of reading again and then he will lock and do its operation.

        * It allows multiple transactions to do read but here version maintaining is done. 

        * So before updation it will first check the version

         
          

