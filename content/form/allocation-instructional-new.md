+++
date = "2016-12-31T23:59:16-05:00"
tags = ["search"]
categories = ["forms"]
images = [""]
author = "Staff"
description = ""
title = "Request an Instructional Allocation"
draft = false
type = "form"
private = true

+++

{{< form-cookies >}}
<form action="https://api.uvarc.io/rest/general-support-request/" method="post" id="allocation-form" accept-charset="UTF-8">
<div class="alert" id="response_message" role="alert" style="padding-bottom:0px;">
  <p id="form_post_response"></p>
</div>
<div>
  <input type="hidden" id="category" name="category" value="Rivanna HPC">
  <input type="hidden" id="allocation_type" name="Allocation Type" value="Instructional Allocation">
  <input type="hidden" id="request_title" name="request_title" value="Allocation Request: Instructional" />
{{% form-userinfo %}}
  <hr size=1 />
  <div class="form-item form-type-select form-group"> <label class="control-label" for="classification">Classification <span class="form-required" title="This field is required.">*</span></label>
    <select required="required" class="form-control form-select required" title="Faculty, postdoctoral associates, and full-time research staff are eligible to request allocations." data-toggle="tooltip" id="classification" name="classification">
    <option value="" selected="selected">- Select -</option>
    <option value="faculty">Faculty</option>
    <option value="staff">Staff</option>
    <option value="postdoc">Postdoctoral Associate</option>
    <option value="other">Other</option></select>
  </div>
  <div class="form-item form-type-textfield form-group"> <label class="control-label" for="department">Department <span class="form-required" title="This field is required.">*</span></label>
    <input required="required" class="form-control form-text required" type="text" id="department" name="department" value="" size="60" maxlength="128" />
  </div>
  <div class="form-item form-type-textfield form-group"> <label class="control-label" for="mygroups-group">Name of MyGroups Account (lowercase only, no spaces) <span class="form-required" title="This field is required.">*</span></label>
    <input required="required" class="form-control form-text required" type="text" id="mygroups-group" name="mygroups-group" value="" size="60" maxlength="128" />
  </div>
  <div class="form-item form-type-textarea form-group"> <label class="control-label" for="mygroup-users">Others to add to MyGroups account (UVA computing IDs separated by commas)</label>
    <div class="form-textarea-wrapper resizable"><textarea class="form-control form-textarea" id="mygroup-users" name="mygroup-users" cols="60" rows="5"></textarea>
    </div>
  </div>
  <div class="row">
    <div class="col form-item form-group form-type-textfield"> <label class="control-label" for="class-id">Class ID <span class="form-required" title="This field is required.">*</span></label>
      <input required="required" class="form-control form-text required" type="text" id="class-id" name="class-id" value="" size="60" maxlength="128" />
    </div>
    <div class="col form-item form-group form-type-textfield"> <label class="control-label" for="academic-term">Academic Term <span class="form-required" title="This field is required.">*</span></label>
      <input required="required" class="form-control form-text required" type="text" id="academic-term" name="academic-term" value="" size="60" maxlength="128" />
    </div>
  </div>
  <div class="row">
    <div class="col form-item form-type-textfield form-group"> <label class="control-label" for="class-size">Class Size <span class="form-required" title="This field is required.">*</span></label>
      <p style="font-size:80%;">How many students are in your class? <br /><br /></p>
      <input required="required" class="form-control form-text required" type="text" id="class-size" name="class-size" value="" size="60" maxlength="128" />
    </div>
    <div class="col form-item form-type-textfield form-group"> <label class="control-label" for="class-schedule">Class Schedule <span class="form-required" title="This field is required.">*</span></label>
      <p style="font-size:80%;">What days/times does this class meet? Enter “n/a” if students will use the cluster at different times.</p>
      <input required="required" class="form-control form-text required" type="text" id="class-schedule" name="class-schedule" value="" size="60" maxlength="128" />
    </div>
  </div>
  <div class="form-item form-type-textarea form-group"> <label class="control-label" for="resources-required">Cores/Memory Required <span class="form-required" title="This field is required.">*</span></label>
    <p style="font-size:80%;">Estimate how many cores and how much memory each student will need to process his/her jobs. General descriptions are fine. A member of our user services team will contact you if we need additional information.</p>
    <div class="form-textarea-wrapper resizable"><textarea class="form-control form-textarea required" id="resources-required" name="resources-required" cols="60" rows="5"></textarea>
    </div>
  </div>
  <input type="hidden" name="details" />
  <div class="form-actions" id="submit-div" style="margin-top:1rem;">
    <hr size="1" style="" />
    <button class="button-primary btn btn-primary form-submit" id="submit" type="submit" name="op" value="Submit">Submit</button>
  </div>
</div>
</form>
<script>
function getParams() {
    var vars = {};
    var parts = window.location.href.replace(/[?&]+([^=&]+)=([^&]*)/gi, function(m,key,value) {
        vars[key] = value;
    });
    return vars;
}
function decode64(str) {
  var e={},i,b=0,c,x,l=0,a,r='',w=String.fromCharCode,L=str.length;
  var A="ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789+/";
  for(i=0;i<64;i++){e[A.charAt(i)]=i;}
  for(x=0;x<L;x++){
    c=e[str.charAt(x)];b=(b<<6)+c;l+=6;
    while(l>=8){((a=(b>>>(l-=8))&0xff)||(x<(L-2)))&&(r+=w(a));}
  }
  return r;
};
var form = document.getElementById('allocation-form');
var cookie_token = getCookie("__user_token");
var url_user_token = getParams()["user_token"];
if (cookie_token !== url_user_token) {
  window.location.replace( "https://auth.uvasomrc.io/site/allocation-instructional-new.php?user_token=" + cookie_token );
}
var name_enc = getParams()["name"];
var name_enc = getParams()["name"];
var uid_enc = getParams()["uid"];
var email_enc = getParams()["email"];
if (name_enc) {
  // do nothing
} else if (uid_enc) {
  // do nothing
} else if (email_enc) {
  // do even more nothing
} else {
  $('#name').val('');
  $('#email').val('');
  $('#uid').val('');
  window.location.replace( "https://auth.uvasomrc.io/site/allocation-instructional-new.php?user_token=" + cookie_token );
}
// name
let name = decodeURI(getParams()["name"]);
let name_dec = decode64(name);
var set_name = document.getElementById("name").value = name_dec;
// uid
let uid = decodeURI(getParams()["uid"]);
let uid_dec = decode64(uid);
var set_uid = document.getElementById("uid").value = uid_dec;
// email
let email = decodeURI(getParams()["email"]);
let email_dec = decode64(email);
var set_email = document.getElementById("email").value = email_dec;
</script>
<script type="text/javascript" src="/js/response-message.js"></script>