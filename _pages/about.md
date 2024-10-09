---
layout: archive
permalink: /
author_profile: true
redirect_from: 
  - /about/
  - /about.html
---
  
I am currently a **PhD student** at LAMSADE (Université Paris Dauphine-PSL, Paris, France) under the supervision of Alexandre Allauzen. I am part of the MILES team which is dedicated to machine learning.

My research is about **frugal machine learning**: I aim at making deep learning models more resource-efficient while maintaining their performance -- the term "resource" referring for instance to time, memory, money, carbon emissions, etc. The PhD focuses mainly on transformers applied to NLP, as they are by far the most resource-consuming models in the field (hello ChatGPT). This is still a very broad topic, and multiple angles of attack are considered -- from the architecture of the model to the optimization algorithm used to train it.

---
<div class="tab-container">
    <div class="tab active-tab" onclick="openTab('tab_news')">News</div>
    <div class="tab" onclick="openTab('tab_publications')">Publications</div>
    <div class="tab" onclick="openTab('tab_career')">Career & Education</div>
</div>

<div id="tab_news" class="tab-content active-content">
    {% include_relative tabs/news.html %}
</div>

<div id="tab_publications" class="tab-content">
    {% include_relative tabs/publications.html %}
</div>

<div id="tab_career" class="tab-content">
    {% include_relative tabs/career.html %}
</div>

<script>
    function openTab(tabId) {
        // Hide all tab contents
        var tabContents = document.getElementsByClassName('tab-content');
        for (var i = 0; i < tabContents.length; i++) {
            tabContents[i].style.display = 'none';
        }

        // Remove 'active-tab' class from all tabs
        var tabs = document.getElementsByClassName('tab');
        for (var i = 0; i < tabs.length; i++) {
            tabs[i].classList.remove('active-tab');
        }

        // Show the selected tab content and mark it as active
        document.getElementById(tabId).style.display = 'block';
        document.querySelector('[onclick="openTab(\'' + tabId + '\')"]').classList.add('active-tab');
    }
</script>

