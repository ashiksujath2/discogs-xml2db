Instructions

1. Converting dumps to csv
python run.py --bz2 --apicounts --export artist --export label --export master --export release --output csvdir --limit=100000 dump-dir

2. Create db tables
python postgresql/psql.py < postgresql/sql/CreateTables.sql

3. Importing data
python postgresql/importcsv.py csvdir/*

4. Set constraints
python postgresql/psql.py < postgresql/sql/CreatePrimaryKeys.sql
python postgresql/psql.py < postgresql/sql/CreateFKConstraints.sql
python postgresql/psql.py < postgresql/sql/CreateIndexes.sql
