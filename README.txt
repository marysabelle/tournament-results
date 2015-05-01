TOURNAMENT PLANNER - Full Stack Web Developer Nanodegree 


PROJECT DESCRIPTION
Python module that uses the PostgreSQL database to keep track of athletes and matches in a game tournament. The game tournament will use the Swiss system for pairing up athletes in each round: athletes are not eliminated, and each athlete should be paired with another athlete with the same number of wins, or as close as possible.

This project has two parts: defining the database schema (SQL table definitions), and writing the code that will use it.


REQUIREMENTS/DEPENDENCIES
 - Python 2.7.9
 - PostgreSQL
 - psycopg2
 - Ubuntu 14.10 on x86_64
 - psql 9.4.1 


FILE - CONTENT
1) tournament.sql: Schema file is located in here; this file contains SQL code that sets up the tournament database for a single tournament.


2) tournament.py: The API to the PostgreSQL instance; includes functions for removing, adding, and editing athletes in the database, and finding Swiss-style parings. 

3) tournament_test.py: Contains unit tests that will test the functions written in tournament.py. Tests can be run from the command line, using the command python tournament_test.py.

4) README.txt: File that includes detail steps required to succesfully run the application.



STEPS TO RUN THIS PROJECT:
Run the program from the command line >> python tournament_test.

if __name__ == '__main__':
 testDeleteMatches()
 testDelete()
 testCount()
 testRegister()
 testRegisterCountDelete()
 testStandingsBeforeMatches()
 testReportMatches()
 testPairings()
 print "Success!  All tests pass!"



And you should be able to see the following output once all tests have passed:

vagrant@vagrant-ubuntu-trusty-32:/vagrant/tournament$ python tournament_test.py
1. Old matches can be deleted.
2. Player records can be deleted.
3. After deleting, countPlayers() returns zero.
4. After registering a player, countPlayers() returns 1.
5. Players can be registered and deleted.
6. Newly registered players appear in the standings with no matches.
7. After a match, players have updated standings.
8. After one match, players with one win are paired.
Success!  All tests pass!
vagrant@vagrant-ubuntu-trusty-32:/vagrant/tournament$


Example of a 16 Player Swiss Tournament:
First round pairing is by random draw. i.e.: With 16 athletes they would be matched into 8 random pairs for the first round. For now, assume all games have a winner, and there are no draws. After the first round, there will be a group of 8 athletes with a score of 1 (win), and a group of 8 athletes with a score of 0 (loss). 

For the 2nd round, athletes in each scoring group will be paired against each other – 1’s versus 1’s and 0’s versus 0’s.
After round 2, there will be three scoring groups:
4 athletes who have won both fights and have 2 points
8 athletes who have won a fight and lost a fight and have 1 point
4 athletes who have lost both fights and have no points.

Again, for round 3, athletes are paired with athletes in their scoring group. After the third round, the typical scoring groups will be:
2 athletes who have won 3 fights (3 points)
6 athletes with 2 wins (2 points)
6 athletes with 1 win (1 point)
2 athletes with no wins (0 points)

For the fourth (and in this case final) round, the process repeats, and athletes are matched with others in their scoring group. Note that there are only 2 athletes who have won all of their fights so far – they will be matched against each other for the "championship" tournament. After the final round, we’ll have something that looks like this:
1 athlete with 4 points – the winner!
4 athletes with 3 points – tied for second place
6 athletes with 2 points
4 athletes with 1 point
1 athlete with 0 points

The Swiss system produces a clear winner in just a few rounds, no-one is eliminated and almost everyone wins at least one game, but there are many ties to deal with.