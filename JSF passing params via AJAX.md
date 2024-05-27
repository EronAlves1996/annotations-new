```xml
<p:selectBooleanCheckbox id="showRecordsToReview" value="#{applicationSession.showRecordsToReview}" required="false"> 
	<f:param name="showRecordsToReviewRefresh" value="true"/> 
	<p:ajax process="@this" event="change" update=":center" partialSubmit="true" /> 
</p:selectBooleanCheckbox>
``` 
