

how to test encoding rule : 

On Ubuntu sys : 
( TO=UTF8 ; ( echo x | sed 's/x/\xd0\xb3\xd0\xb2\xd0\xb9/' ) > test1 ; iconv -f utf8 -t "$TO" test1 | od -tx1 ; iconv -f gb18030 -t "$TO" test1 | od -tx1 ; iconv -f iso88591 -t "$TO" test1 | od -tx1 ; iconv -f utf8 -t "$TO" test1 ; iconv -f gb18030 -t "$TO" test1 ; iconv -f iso88591 -t "$TO" test1


on OSX : 
( TO=UTF8 ; ( echo x | sed $'s/x/\xd0\xb3\xd0\xb2\xd0\xb9/' ) > test1 ; iconv -f utf8 -t "$TO" test1 | od -tx1 ; iconv -f gb18030 -t "$TO" test1 | od -tx1 ; iconv -f iso-8859-1 -t "$TO" test1 | od -tx1 ; iconv -f utf8 -t "$TO" test1 ; iconv -f gb18030 -t "$TO" test1 ; iconv -f iso-8859-1 -t "$TO" test1 ) 


You will see 6 first lines are a check that you may consider this binary file (test1) as encoded UTF8 / GB18030 and ISO-8859-1 without error. 

Conclusion : 
You cannot guess by check  how the file is encoded.


the 3 last lines let you show what would be the content following different encoding rule, let's guess what choice is the right one :-)

