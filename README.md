# check for duplicate answers within a survey, particularly in the context of iterations.
OSM.Survey.FnDuplicateAnswers = function(e) {

OSM.NotificationSystem.hideAllNotifications();
var myCheck = e.sourceElement.getAnswers();
var myItrName = e.sourceElement.parent().get("objectName");
var ans;
var bCheck = true;
e.sourceElement.parent().parent().getVisibleIterations().forEach( function(iteration){
    ans = iteration[e.sourceElement.get("objectName")].getAnswers();
    if(ans == myCheck&& myItrName !== iteration.get("objectName")){ bCheck = false; this.break();
        
} });
if(bCheck) {
    return {status:true}; 
    
} else { 
    return {status:false, message: "Duplicate ranking!"};
    } 
}
