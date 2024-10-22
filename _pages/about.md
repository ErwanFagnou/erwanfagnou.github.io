---
layout: main_page
permalink: /
redirect_from: 
  - /about/
  - /about.html
---

<!-- Picture and short bio -->
<div style="display: flex; align-items: center; margin-bottom: 30px; margin-left: 5%; margin-right: 5%">
    <!-- Picture -->
    <div style="width: 300px; display: inline-block">
        <img src="{{ site.author.avatar | prepend: "/images/" | prepend: base_path }}" alt={{ site.author.name }} style="max-height: 250px">
    </div>
    <!-- Short bio -->
    <div style="width: 90%; display: inline-block; margin-left: 50px">  
        <p>I am currently a <strong>PhD student</strong> at LAMSADE (Université Paris Dauphine-PSL, Paris, France) under the supervision of Alexandre Allauzen. I am part of the MILES team which is dedicated to machine learning. </p>
        <p>My research is about <strong>frugal machine learning</strong>: I aim at making deep learning models more resource-efficient while maintaining their performance — the term "resource" referring for instance to time, memory, money, carbon emissions, etc. The PhD focuses mainly on transformers applied to NLP, as they are by far the most resource-consuming models in the field (hello ChatGPT). This is still a very broad topic, and multiple angles of attack are considered — from the architecture of the model to the optimization algorithm used to train it.</p>
    </div>
</div>
 
<!-- Contact info -->
<div style="display: flex; justify-content: center; align-items: center;">
    <div style="display: flex; justify-content: space-between; align-items: flex-start; width: 70%">
        <!-- Left Column -->
        <div style="width: 48%;">
            <!-- Email -->
            <div style="display: flex; align-items: center; margin-bottom: 10px;">
                <i class="fas fa-fw fa-envelope" aria-hidden="true" style="margin-right: 10px"></i>
                <span>{{ site.author.email }}</span>
            </div>
            <!-- Google Scholar -->
            <div style="display: flex; align-items: center; margin-bottom: 10px;">
                <i class="fas fa-fw fa-graduation-cap" style="margin-right: 10px"></i>
                <a href="{{ site.author.googlescholar }}" target="_blank">Google Scholar</a>
            </div>
        </div>
        <!-- Right Column (Location) -->
        <div style="width: 48%;">
            <div style="display: flex; align-items: flex-start;">
                <i class="fa fa-fw fa-map-marker" aria-hidden="true" style="margin-right: 10px; margin-top: 2px;"></i>
                <div style="text-align: left;"> {{ site.author.location }} </div>
            </div>
        </div>
    </div>
</div>


---

<!-- Menu for all tabs -->
<div class="tab-container">
    <div class="tab active-tab" onclick="openTab('tab_news')">News</div>
    <div class="tab" onclick="openTab('tab_publications')">Publications</div>
    <div class="tab" onclick="openTab('tab_career')">Career & Education</div>
</div>

<div style="height: 6px; background-color: rgb(86, 149, 179); margin-bottom: 4px;"></div>

<!-- Tab contents, showing only the one selected -->
<div id="tab_news" class="tab-content active-content">{% include_relative tabs/news.html %}</div>
<div id="tab_publications" class="tab-content">{% include_relative tabs/publications.html %}</div>
<div id="tab_career" class="tab-content">{% include_relative tabs/career.html %}</div>

<script>
    function openTab(tabId) {
        /* Hide all tab contents */
        var tabContents = document.getElementsByClassName('tab-content');
        for (var i = 0; i < tabContents.length; i++) {
            tabContents[i].style.display = 'none';
        }

        /* Remove 'active-tab' class from all tabs */
        var tabs = document.getElementsByClassName('tab');
        for (var i = 0; i < tabs.length; i++) {
            tabs[i].classList.remove('active-tab');
        }

        /* Show the selected tab content and mark it as active */
        document.getElementById(tabId).style.display = 'block';
        document.querySelector('[onclick="openTab(\'' + tabId + '\')"]').classList.add('active-tab');
    }
</script>

