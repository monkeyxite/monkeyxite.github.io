<html><body><div><span class="Apple-style-span" style="font-weight:bold;"><span class="Apple-style-span" style="font-size:large;">Procedure</span></span></div><div><span class="Apple-style-span" style="font-weight:bold;">
</span></div><div>Q:</div><div><a href="http://www.pythonchallenge.com/pc/def/map.html">http://www.pythonchallenge.com/pc/def/map.html</a>
</div><div>
</div><div>A:
<pre class="python">s = "g fmnc wms bgblr rpylqjyrc gr zw fylb. rfyrq ufyr amknsrcpq ypc dmp. bmgle gr gl zw fylb gq glcddgagclr ylb rfyr'q ufw rfgq rcvr gq qm jmle. sqgle qrpgle.kyicrpylq() gq pcamkkclbcb. lmu ynnjw ml rfc spj."
def trans(s1, s2=""):
   for i in s1:
       if i in " .,'":
           s2 += i
       elif i is "y":
           s2 += "a"
       elif i is "z":
           s2 += "b"
       else:
           s2 += chr(ord(i) + 2 )
   return s2

print trans(s)
</pre><div><a href="http://www.pythonchallenge.com/pcc/def/ocr.html">Other Answer</a></div><div>
</div><div>
</div><div><span class="Apple-style-span" style="font-weight:bold;"><span class="Apple-style-span" style="font-size:large;">Conclusion</span></span></div><div><span class="Apple-style-span" style="font-weight:bold;">
</span></div><div>I think mine is straight, redundance, complex, and does not use the power of standard lib. </div><div>
</div><div>Lessons learned:  </div><div><ol><li>DRY
</li><li>string module</li></ol><div>
</div><div><span class="Apple-style-span" style="font-weight:bold;"><span class="Apple-style-span" style="font-size:large;">Review</span></span></div><div><span class="Apple-style-span" style="font-weight:bold;">
</span></div><div><span class="Apple-style-span" style="font-size:medium;">N/A</span></div></div></div></body></html>