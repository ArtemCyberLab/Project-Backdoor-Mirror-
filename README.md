A website required authentication to access a hidden flag. By inspecting the page through "View Page Source," I discovered a JavaScript authentication script. The code explicitly contained the username h3ck3rBoi and a strange password 54321@terceSrepuS, which turned out to be written in reverse. Using a string reversal method, I restored the correct password as SuperSecret@12345. Entering these credentials allowed the site to make a request to a hidden file RandomLo0o0o0o0o0o0o0o0o0gpath12345_Flag_h3ck3rBoi_SuperSecret@12345.txt, which contained the coveted flag.

This case demonstrated serious security flaws in the web application: storing credentials in client-side code, weak password protection, and a predictable structure for hidden file paths. To prevent such vulnerabilities, the site should have implemented server-side password validation, data hashing, and secure authentication methods. This example clearly illustrated how insufficient protection can lead to a breach without requiring complex attacks.

<script>
    function authenticate() {
        a = document.getElementById('uname');
        b = document.getElementById('pass');
        const RevereString = str => [...str].reverse().join('');
        if (a.value=="h3ck3rBoi" & b.value==RevereString("54321@terceSrepuS")) { 
            var xhttp = new XMLHttpRequest();
            xhttp.onreadystatechange = function() {
                if (this.readyState == 4 && this.status == 200) {
                    document.getElementById("flag").innerHTML = this.responseText;
                    document.getElementById("todel").innerHTML = "";
                    document.getElementById("rm").remove();
                }
            };
            xhttp.open("GET", "RandomLo0o0o0o0o0o0o0o0o0gpath12345_Flag_"+a.value+"_"+b.value+".txt", true);
            xhttp.send();
        }
    }
</script>
