PSQL="psql --username=freecodecamp --dbname=periodic_table -t --no-align -c"


INPUT=$1
LEN=${#INPUT}
if [[ -z $INPUT ]]
then
  echo "Please provide an element as an argument."
else
  if [[ ! $INPUT =~ ^[0-9]+$ ]]
  then
    if [ $LEN -gt 2 ]
    then
      OUTPUT=$($PSQL "SELECT * FROM elements WHERE name='$INPUT'")
      if [[ -z $OUTPUT ]]
      then
        echo "I could not find that element in the database."
      else
        ATOMIC_NUM=$($PSQL "SELECT atomic_number FROM elements WHERE name='$INPUT'")
        NAME=$($PSQL "SELECT name FROM elements WHERE name='$INPUT'")
        SYMBOL=$($PSQL "SELECT symbol FROM elements WHERE name='$INPUT'")
        TYPE=$($PSQL "SELECT type FROM properties INNER JOIN types USING(type_id) WHERE atomic_number=$ATOMIC_NUM")
        ATOMIC_MASS=$($PSQL "SELECT atomic_mass FROM properties WHERE atomic_number=$ATOMIC_NUM")
        MELTING_P=$($PSQL "SELECT melting_point_celsius FROM properties WHERE atomic_number=$ATOMIC_NUM")
        BOILING_P=$($PSQL "SELECT boiling_point_celsius FROM properties WHERE atomic_number=$ATOMIC_NUM")
        echo "The element with atomic number $ATOMIC_NUM is $NAME ($SYMBOL). It's a $TYPE, with a mass of $ATOMIC_MASS amu. $NAME has a melting point of $MELTING_P celsius and a boiling point of $BOILING_P celsius."
      fi
    else
      OUTPUT=$($PSQL "SELECT * FROM elements WHERE symbol='$INPUT'")
      if [[ -z $OUTPUT ]]
      then
        echo -e "\nI could not find that element in the database.\n"
      else
        ATOMIC_NUM=$($PSQL "SELECT atomic_number FROM elements WHERE symbol='$INPUT'")
        NAME=$($PSQL "SELECT name FROM elements WHERE symbol='$INPUT'")
        SYMBOL=$($PSQL "SELECT symbol FROM elements WHERE symbol='$INPUT'")
        TYPE=$($PSQL "SELECT type FROM properties INNER JOIN types USING(type_id) WHERE atomic_number=$ATOMIC_NUM")
        ATOMIC_MASS=$($PSQL "SELECT atomic_mass FROM properties WHERE atomic_number=$ATOMIC_NUM")
        MELTING_P=$($PSQL "SELECT melting_point_celsius FROM properties WHERE atomic_number=$ATOMIC_NUM")
        BOILING_P=$($PSQL "SELECT boiling_point_celsius FROM properties WHERE atomic_number=$ATOMIC_NUM")
        echo "The element with atomic number $ATOMIC_NUM is $NAME ($SYMBOL). It's a $TYPE, with a mass of $ATOMIC_MASS amu. $NAME has a melting point of $MELTING_P celsius and a boiling point of $BOILING_P celsius."
      fi
    fi  
  else
    OUTPUT=$($PSQL "SELECT * FROM elements WHERE atomic_number='$INPUT'")
    if [[ -z $OUTPUT ]]
    then
      echo -e "\nI could not find that element in the database.\n"
    else
        ATOMIC_NUM=$($PSQL "SELECT atomic_number FROM elements WHERE atomic_number='$INPUT'")
        NAME=$($PSQL "SELECT name FROM elements WHERE atomic_number='$INPUT'")
        SYMBOL=$($PSQL "SELECT symbol FROM elements WHERE atomic_number='$INPUT'")
        TYPE=$($PSQL "SELECT type FROM properties INNER JOIN types USING(type_id) WHERE atomic_number=$ATOMIC_NUM")
        ATOMIC_MASS=$($PSQL "SELECT atomic_mass FROM properties WHERE atomic_number=$ATOMIC_NUM")
        MELTING_P=$($PSQL "SELECT melting_point_celsius FROM properties WHERE atomic_number=$ATOMIC_NUM")
        BOILING_P=$($PSQL "SELECT boiling_point_celsius FROM properties WHERE atomic_number=$ATOMIC_NUM")
        echo "The element with atomic number $ATOMIC_NUM is $NAME ($SYMBOL). It's a $TYPE, with a mass of $ATOMIC_MASS amu. $NAME has a melting point of $MELTING_P celsius and a boiling point of $BOILING_P celsius."
      fi
  fi
fi
