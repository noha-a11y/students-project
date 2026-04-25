<?php
$students = array(
    array(
        "name" => "noha",
        "grade" => 99,
        "age" => 21,
    ),

    array(
        "name" => "ssoso",
        "grade" => 80,
        "age" => 22,

    ),

    array(
        "name" => "Mustafa",
        "grade" => 55,
        "age" => 23,

    ),

    array(

        "name" => "Muhammad",
        "grade" => 70,
        "age" => 24,


    ),

    array(

        "name" => "Hassan",
        "grade" => 56,
        "age" => 25,
    )

);




function calculateStatus($grade)
{

    if ($grade >= 90) {
        return "ممتاز";
    } elseif ($grade >= 80) {
        return "جيد جدا";
    } elseif ($grade >= 70) {
        return "جيد";
    } elseif ($grade >= 60) {
        return "مقبول";
    } else {
        return "راسب";
    }
}


$max = $students[0]["grade"];
$min = $students[0]["grade"];
$sum = 0;
$passedCount = 0;

function calculateStatistics($students)
{
    $max = $students[0]["grade"];
    $min = $students[0]["grade"];
    $sum = 0;
    $passedCount = 0;

    foreach ($students as $student) {

        $grade = $student["grade"];

        if ($grade > $max) $max = $grade;
        if ($grade < $min) $min = $grade;

        $sum += $grade;

        if ($grade >= 60) $passedCount++;
    }

    return [
        "max" => $max,
        "min" => $min,
        "average" => $sum / count($students),
        "passed" => $passedCount
    ];
}

// حساب المعدل
$stats = calculateStatistics($students);



?>


<html>

<head>
    <title>php</title>
</head>

<body>

    <?php
    //     echo date("Y/M/D"); 
    ?>
    <!-- //     <br> <br> -->
    // <?php // echo date("h/i/sa");  
        ?>
    <!-- //     <br> <br> -->

    // <?php
        //    date_default_timezone_set("Africa/Cairo");
        //    echo "الوقت في مصر: " . date("Y-m-d h:i:s") . "<br>";
        //     
        ?>
    <!-- //     <br> <br> -->


    // <?php
        //    date_default_timezone_set("Asia/Kolkata");
        //    echo "الوقت في الهند: " . date("Y-m-d h:i:s");
        //     
        ?>
    <!-- //     <br> <br> -->


    // <?php
        //    date_default_timezone_set("Asia/Gaza");
        //    echo "غزه : " . date("Y-m-d h:i:s");
        ?>


    <table border="2px">
        <tr>
            <td>name</td>
            <td>grade</td>
            <td>age</td>
            <td>الحاله</td>
        </tr>

        <?php foreach ($students as $student) { ?>
            <tr>
                <td><?php echo $student["name"]  ?></td>
                <td><?php echo $student["age"]  ?></td>
                <td><?php echo $student["grade"]  ?></td>
                <td><?php echo calculateStatus($student["grade"])  ?></td>
            </tr>


        <?php } ?>

    </table>

    <br>

    <table border="2px">
    <tr>
        <td>أعلى درجة</td>
        <td>أقل درجة</td>
        <td>المعدل</td>
        <td>عدد الناجحين</td>
    </tr>

    <tr>
        <td><?php echo $stats["max"]; ?></td>
        <td><?php echo $stats["min"]; ?></td>
        <td><?php echo number_format($stats["average"], 2); ?></td>
        <td><?php echo $stats["passed"]; ?></td>
    </tr>
</table>
</body>

</html>
