For loop


function fetchform($URI)
{

if ($this->fetch($URI))
{

if(is_array($this->results))
{
for($x=0;$x<count($this->results);$x++)
$this->results[$x] = $this->_stripform($this->results[$x]);
}
else
$this->results = $this->_stripform($this->results);

return true;
}
else
return false;
}

// Fetchform continiues to if this fetch
    // If this fetch is true, is_array the results into for loop
        //For x = 0, + 1 each time it loops, until it reaches it's count
    //Else if the fetch is false, result becomes stripform, and  return true
//Else return false