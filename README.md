# Floating-Label
Floating label is a small jquery code for label effect for input fields like material design.
When input field get focus then related lable floats to up and floats down on field blur if the field is empty.

# Dependency
jQuery library is required to make it funtioning and should be included on top.

# HTML markup
A basic html markup to create input field sturcture.

<pre>
  <code>
  &lt;div class="md-input-wrap"&gt;
     &lt;input type="text" id="phone" class="md-input form-control"&gt;
       &lt;label for="phone"&gt;Phone&lt;/label&gt;
  &lt;/div&gt;
  </code>
</pre>

# CSS
CSS for styling and positioning of the elements.

<pre>
  <code>
  .md-input:focus{
     border-color: #f23d18;
}
.md-input:focus + label,.md-input.md-hastext + label{
     color: #f23d18;
     top: 0%;
     font-size: 0.75em;
}
.md-input-wrap {
  margin-top: 20px;
  padding-top: 10px;
  position: relative;
}
.md-input-wrap label {
  left: 0;
  position: absolute;
  top: calc(50% + 5px);
  transform: translateY(-50%);
  transition: all 0.15s ease-in-out 0s;
  color: #000;
}
.md-input-wrap::after {
  background-color: #f23d18;
  content: "";
  height: 2px;
  left: 0;
  position: absolute;
  top: 100%;
  width: 0%;
  transition: all 0.15s ease-in-out 0s;
}
.md-input-wrap::before {
  background-color: #e5e5e5;
  content: "";
  height: 2px;
  left: 0;
  position: absolute;
  top: 100%;
  width: 100%;
}
.md-input-wrap.md-hastext::after{
     width: 100%;
}
.md-input-wrap .md-input{
     width: 100%;
     border:0;
     height: 30px;
}
  </code>
</pre>

# jQuery
Basic jQuery is required to make it functioning.

<pre>
  <code>
  var input = $(".md-input");
  input.on("blur",function(){
       if($(this).parent().hasClass("md-input-wrap")){
            if($(this).val()!==''){
                 $(this).addClass('md-hastext');
                 $(this).parent(".md-input-wrap").addClass("md-hastext");
            }else{
                 $(this).removeClass('md-hastext');
                 $(this).parent(".md-input-wrap").removeClass("md-hastext");
            }
       }
  });
  input.on("focus",function(){
       if($(this).parent().hasClass("md-input-wrap")){
            $(this).parent(".md-input-wrap").addClass("md-hastext");
       }
  });
  </code>
</pre>
