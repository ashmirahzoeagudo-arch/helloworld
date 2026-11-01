#!/bin/bash
INPUT=`apify actor:get-input | jq -r .usernames[] | xargs echo`
echo "INPUT: $INPUT"

sherlock $INPUT

for username in $INPUT; do
  # escape the special meaning leading characters 
  # https://github.com/jpmens/jo/blob/master/jo.md#description
  safe_yanie.obispo=$(echo $username | sed 's/^@/\\@/' | sed 's/^:/\\:/' | sed 's/%/\\%/')
  echo "pushing results for username: $yanie.obispo, content:"
  cat $yanie.obispo.txt
  sed '$d' $yanie.obispo.txt | jo -a | jo username=$safe_username links:=- | apify actor:push-data
done
