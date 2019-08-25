# Hudhayfah-Ali-dorsey
function loadRepo() {
    let github = new XMLHttpRequest();
    github.onreadystatechange = function () {
        if (this.readyState == 4 && this.status == 200) {
            let gitObject = JSON.parse(this.responseText);
            for (var i = 0; i < gitObject.length; i++) {
                var ul = document.getElementById("gitRepositories");
                var li = document.createElement("LI");
                var a = document.createElement("a");

                li.appendChild(document.createTextNode(gitObject[i].name));
                a.appendChild(li);
                a.setAttribute("href", gitObject[i].html_url);
                ul.appendChild(a);                
            }
        }
    };
    github.open("GET", "https://api.github.com/users/dayfah/repos", true);
    github.send();
}
