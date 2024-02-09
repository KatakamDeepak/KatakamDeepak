- 👋 Hi, I’m @KatakamDeepak
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...
- 😄 Pronouns: ...
- ⚡ Fun fact: ...

<!---
KatakamDeepak/KatakamDeepak is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->


<?php

  $num = readline("Enter the number: ");
  echo "Multiplication table of ",$num," is\n\n";     
  for ($i = 1; $i <= 10; $i++) {
    echo "\t", $num, " x ", $i, " = ", $num * $i, "\n";
  }
  
?>

<!DOCTYPE html>
<html lang="en">
<head>
    <title>check year is leap year or not</title>
</head>
<body>
    <form>
       <label> Enter the Year </label> <input type="number" name="LeapYear">
    <input type="submit" value="submit" name="submitForm"></br></br>
    </form>
</body>
</html>
<?php
if(isset($_GET["submitForm"]))
{
    $year=$_GET['LeapYear'];
    if(($year%4)==0)
    {
        if(($year%100)==0)
        {
            if(($year%400)==0)
            {
                echo "$year is a leap year";
            }
            else{
                echo "$year is not a leap year";
            }
        }
        else{
            echo "$year is a leap year";
        }
    }
    else{
        echo "$year is not a leap year";
    }
}
?>





<!DOCTYPE html>
<html>
<body>

<form action="upload.php" method="post" enctype="multipart/form-data">
  Select image to upload:
  <input type="file" name="fileToUpload" id="fileToUpload">
  <input type="submit" value="Upload Image" name="submit">
</form>

</body>
</html>
<?php
$target_dir = "uploads/";
$target_file = $target_dir . basename($_FILES["fileToUpload"]["name"]);
$uploadOk = 1;
$imageFileType = strtolower(pathinfo($target_file,PATHINFO_EXTENSION));
// Check if image file is a actual image or fake image
if(isset($_POST["submit"])) {
  $check = getimagesize($_FILES["fileToUpload"]["tmp_name"]);
  if($check !== false) {
    echo "File is an image - " . $check["mime"] . ".";
    $uploadOk = 1;
  } else {
    echo "File is not an image.";
    $uploadOk = 0;
  }
}
?>
// Check if file already exists
if (file_exists($target_file)) {
  echo "Sorry, file already exists.";
  $uploadOk = 0;
}
// Check file size
if ($_FILES["fileToUpload"]["size"] > 500000) {
  echo "Sorry, your file is too large.";
  $uploadOk = 0;
}
// Allow certain file formats
if($imageFileType != "jpg" && $imageFileType != "png" && $imageFileType != "jpeg"
&& $imageFileType != "gif" ) {
  echo "Sorry, only JPG, JPEG, PNG & GIF files are allowed.";
  $uploadOk = 0;
}
