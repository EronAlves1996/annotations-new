```xml
<!-- Wrap all the elements that wants to disable with this tag, based on a param conditional -->
 <f:validateBean disabled="#{not empty param.disableValidation and param.disableValidation}">
          <p:selectOneMenu id="comboPais" widgetVar="comboPaisWV" value="#{action.pais}" style="width:180px" styleClass="inputMargin6">
            <f:selectItem itemLabel="#{bundle.lblSelecionarCombo}" itemValue="#{null}"/>
            <f:selectItems value="#{items_Pais}" />
            
            <!-- The ajax is tied to the selecting an element. Declare the param as the same on the condition on top -->
            <f:param name="disableValidation" value="true" />
            <p:ajax update="comboEstado comboCidade" listener="#{action.updatePais}" />
          </p:selectOneMenu>
      <div class="row">
        <div class="col-sm-4">
          <p:outputLabel id="labelEstado" value="#{bundle.lblEstado}:" for="comboEstado" indicateRequired="true"/><br />
          <p:selectOneMenu id="comboEstado" widgetVar="comboEstadoWV" value="#{action.estado}" style="width:200px" styleClass="inputMargin6">
            <f:selectItem itemLabel="#{bundle.lblSelecionarCombo}" itemValue="#{null}"/>
            <f:selectItems value="#{action.estados}" var="item" itemLabel="#{item.nome}" itemValue="#{item}"/>
            <f:param name="disableValidation" value="true" />
            <p:ajax update="comboCidade" listener="#{action.updateEstado}" />
          </p:selectOneMenu>
        </div>
        <div class="col-sm-4">
          <p:outputLabel id="labelCidade" value="#{bundle.lblCidade}:" for="comboCidade" /><br />
          <p:selectOneMenu id="comboCidade" widgetVar="comboCidadeWV" value="#{action.municipio}" style="width:200px" styleClass="inputMargin6">
            <f:selectItem itemLabel="#{bundle.lblSelecionarCombo}" itemValue="#{null}"/>
            <f:selectItems value="#{action.municipios}" var="item" itemLabel="#{item.nome}" itemValue="#{item}"/>
          </p:selectOneMenu>
        </div>
        <div class="col-sm-4">
          <p:outputLabel id="labelModalidadeOcupacao" value="#{bundle.lblModalidadeOcupacao}:" for="comboModalidadeOcupacao" /><br />
          <p:selectOneMenu id="comboModalidadeOcupacao" widgetVar="comboModalidadeOcupacaoWV" value="#{action.item.modalidadeOcupacao}" style="width:180px" styleClass="inputMargin6">
            <f:selectItem itemLabel="#{bundle.lblSelecionarCombo}" itemValue="#{null}"/>
            <f:selectItems value="#{items_ModalidadeOcupacao}" />
          </p:selectOneMenu>
        </div>
      </div>
      </f:validateBean>
```
