# reverse-
unc _GetDelim($sTest)     If Not IsString($sTest) Then Return SetError(1, 0, "") ; Invalid Input String.      Local $aAscII[31], $sDelim ; Using Control Characters only.     ; First try one character     For $i = 1 To 31         $sDelim = Chr($i)         If Not StringInStr($sTest, $sDelim, 1) Then             Return $sDelim         Else             $aAscII[$i - 1] = $sDelim ; Needed for the next stage.         EndIf     Next      ; That failed - so we try two characters.     Local $aDoubleChar = _ArrayCombinations($aAscII, 2, "")     For $i = 1 To $aDoubleChar[0]         $sDelim = $aDoubleChar[$i]         If Not StringInStr($sTest, $sDelim, 1) Then Return $sDelim     Next      ; That failed - so we try the reverse patterns.     ReDim $aDoubleChar[931]     $aDoubleChar[0] = 930
