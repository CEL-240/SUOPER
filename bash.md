#1
Create a script that will perform the following actions:

    Print all lines from the file specified as "filename" file to standard output that are not blank lines and are not comments.
    Comments are lines which include a '#' as the first character.
    Do not print anything else to standard output for this question.
    The format of the input file will be similar to that of the /etc/hosts file.

function q1()
{
  #Valid Variables are:
  filename=$1
  #You code here
}

function q1()
{
  #Valid Variables are:
  filename=$1
  #You code here
  grep -vE "^\s*($|#)" "$filename"
}

----------------------------------------------------------------------------------------------------------
#2


Create a script that will perform the following actions:

    Locate all files that end in ".log" in the specified directory by "logs"
    Create an archive of those files in a gzipped tar ball
    Store the gzipped tar ball as the file name specified in "archive"

function q1()
{
  #Valid Variables are:
  logs=$1
  archive=$2
  #Your code here
}

function q1()
{
  #Valid Variables are:
  logs=$1
  archive=$2
  #Your code here
  tar -czf "$archive" -C "$logs" $(find "$logs" -type f -name "*.log" -printf "%P\n")
}










---------------------------------------------------------------------------------------------------------------
#3



Create a script that will perform the following actions:

    Locate all files in the directory "searchdir" that contain the case insensitive text "CRITICAL".
    Write all the filenames with path into a file specified by argument "output".

IMPORTANT NOTE: The contents of the file are what matter, not the filename. No filenames will contain critical.

function q1()
{
  #Valid Variables are:
  searchdir=$1
  output=$2
  #Your code here
}

function q1() {
  # Valid Variables are:
  searchdir=$1
  output=$2

  # Your code here
  find "$searchdir" -type f | while read -r file; do
    if grep -qi "CRITICAL" "$file"; then
      echo "$file"
    fi
  done >> "$output"
}




----------------------------------------------------------------------------------------------
#4




Create a script that will perform the following actions:

    Given a space separated list of directories in "dirlist", your code will obtain the total number of files in all the directories. Subdirectories will NOT be included in the total.
    Print to standard output the total number of files

function q1()
{
  #Valid Variables are:
  dirlist=$1
  #You code here
}

function q1()
{
  dirlist=$1

  total_files=0

  for dir in $dirlist; do
    if [ -d "$dir" ]; then

      num_files=$(ls -l "$dir" | grep -c '^-')
      # Add the count to the total
      total_files=$((total_files + num_files))
    else
      echo "Directory $dir does not exist."
    fi
  done
  echo $total_files
}


------------------------------------------------------------------------------------
#5





Create a script that will perform the following actions:

    Delete all files contained in the directory specified by "dirdel"
    Do not delete the directory specified by "dirdel"

function q1()
{
  #Valid Variables are:
  dirdel=$1
  #Your code here
}

function q1()
{
  # Valid Variables are:
  dirdel=$1
  find "$dirdel" -mindepth 1 -type f -delete
}





-----------------------------------------------------------------------------------
#6


Create a script that will perform the following actions:

    Create a file specified by the name contained in parameter "newfile"
    Set the modified date of the file to June 14, of the current year
    Set the modified time to the file to 0830

function q1()
{
  #Valid Variables are:
  newfile=$1
  #Your code here
}


function q1()
{
  # Valid Variables are:
  newfile=$1
  touch "$newfile"
  current_year=$(date +%Y)
  touch -t "${current_year}06140830" "$newfile"
}




--------------------------------------------------------------------------------------
#7


Create a script that will perform the following actions:

    Read the file specified by "filename" and perform an action based on the contents of the file
    If the contents of the file are "abc", print "123" to standard output
    If the contents of the file are "def", print "789" to standard output
    If the contents of the file are "xyz", print "000" to standard output
    If the contents of the file are not "abc", "def", or "xyz", print "Error" to standard output

function q1()
{
  #Valid Variables are:
  filename=$1
  #Your code here
}



function q1()
{
  # Valid Variables are:
  filename=$1

  # Your code here
  content=$(<"$filename")

  
  if [[ $content == "abc" ]]; then
      echo "123"
  elif [[ $content == "def" ]]; then
      echo "789"
  elif [[ $content == "xyz" ]]; then
      echo "000"
  else
      echo "Error"
  fi
}


--------------------------------------------------------------------------------------
#8




Create a script that will perform the following actions: Copy all lines from the file specified by "src" to the file specified by "dst" which contain the text specified by "match"

function q1()
{
  #Valid Variables are:
  src=$1
  dst=$2
  match=$3
  #Your code here
}


function q1()
{
  #Valid Variables are:
  src=$1
  dst=$2
  match=$3
  #Your code here
  cat $src | grep $match > $dst
}




--------------------------------------------------------------------------------------
#9


Create a script that will perform the following actions:

    Terminate the process that has the name specified by 'var'.
    The name of the process in 'var' varies and will change each time the application is run

function q1()
{
  #Valid Variables are:
  var=$1
  #Your code here
}



function q1()
{
  #Valid Variables are:
  var=$1
  #Your code here
  pkill "$var"
}


--------------------------------------------------------------------------------------
#10



Create a script that will perform the following actions:

    Given a directory specified by "dirpath" create a sorted list of all files in the directory that were modified within the previous hour.
    Ensure that the full path to each file is used for the sort and is included in the output.
    The list should include all files in the specified directory and any subdirectories.
    Print this list to the screen, one item on each line.

function q1()
{
  #Valid Variables are:
  dirpath=$1
  #Your code here
}

function q1()
{
  #Valid Variables are:
  dirpath=$1
  #Your code here
  find "$dirpath" -type f -mmin -60 -printf "%p\n" | sort
}


