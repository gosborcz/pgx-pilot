# pgx-pilot

` awk -F'\t' -vOFS='\t' '{ gsub("MIN_DP", "DP", $9) ; print }' ` replace MIN_DP with DP


(error: Caused by: org.pharmgkb.pharmcat.ParseException: Problem at chr1:97515686:
Don't know how to handle alt structural variant '<NON_REF>')
