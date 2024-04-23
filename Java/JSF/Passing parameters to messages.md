```xml
<h:outputFormat value="#{msg['message.param1']}">
   <f:param value="param0" />
</h:outputFormat>
<h:outputFormat value="#{msg['message.param2']}">
   <f:param value="param0" />
   <f:param value="param1" />
</h:outputFormat>

```

```toml
// properties

message.param1 = This is "message.param1" - {0}
message.param2 = This is "message.param2" - {0} and {1}
```