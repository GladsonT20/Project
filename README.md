# Projectfunction getmarks($c, $s, $t){
             include('connect.php');
     	     $resultm = $db->prepare("SELECT subject.NameOfSubject, result.marks FROM result INNER JOIN subject on result.stubjectid=subject.stubjectid WHERE result.classid='$c' AND result.stdid='$s' AND result.typleofexam='$t'");
             //$result->bindParam(':id', $m);
             $resultm->execute();
	       for($i=0; $rowresult= $resultm->fetch(); $i++)
	          { 
	          	echo "<td>";
	          	echo $rowresult['NameOfSubject'];
	          	echo "</td>";
               }
             }
 function getmarkss($c, $s, $t){
             include('connect.php');
     	     $resultm = $db->prepare("SELECT subject.NameOfSubject, result.marks FROM result INNER JOIN subject on result.stubjectid=subject.stubjectid WHERE result.classid='$c' AND result.stdid='$s' AND result.typleofexam='$t'");
             //$result->bindParam(':id', $m);
             $resultm->execute();
	       for($i=0; $rowresult= $resultm->fetch(); $i++)
	          { 
	          echo "<td>";
             echo $rowresult['marks'];
	         	if($rowresult['marks'] >= 81){
                 echo "[A]";
	         	}elseif ($rowresult['marks']>=61 && $rowresult['marks']<=80) {
	         		 echo "[B]";
	         	}
	         	elseif ($rowresult['marks']>=41 && $rowresult['marks']<=60) {
	         		 echo "[C]";
	         	}
	         	elseif ($rowresult['marks']>=31 && $rowresult['marks']<=40) {
	         		 echo "[D]";
	         	}
	         	elseif ($rowresult['marks']>=21 && $rowresult['marks']<=30) {
	         		 echo "[E]";
	         	}
	         	elseif ($rowresult['marks']<=20) {
	         		 echo "[F]";
	         	}
	         	echo "</td>";
	         	 }

             }
             function gettotalmarks($e, $g, $y){
             	 include('connect.php');
             	$resultg = $db->prepare("SELECT SUM(result.marks) as totalmark FROM result INNER JOIN subject on result.stubjectid=subject.stubjectid WHERE result.classid='$e' AND result.stdid='$g' AND result.typleofexam='$y'");
             $resultg->execute();
             $rowt = $resultg->fetch(PDO::FETCH_ASSOC);
             echo "<td>";
             echo $rowt['totalmark'];
             echo "</td>";
             }
                function getaveragemarks($m, $j, $k){
             	 include('connect.php');
             	$resulta = $db->prepare("SELECT ROUND(AVG(result.marks), 1) as aver FROM result INNER JOIN subject on result.stubjectid=subject.stubjectid WHERE result.classid='$m' AND result.stdid='$j' AND result.typleofexam='$k'");
             $resulta->execute();
             $rowa = $resulta->fetch(PDO::FETCH_ASSOC);
             echo "<td>";
             echo $rowa['aver'];
             echo "</td>";
             }
				?>
