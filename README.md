EclipselinkLogger
=================

EclipselinkLogger with JPA 2


Realiza gravação do Log seguindo as configurações do log4j.xml


persistence.xml
	Incluia:
		<property name="eclipselink.logging.logger" value="org.eclipse.persistence.logging.CommonsLoggingSessionLog"/>
		
		
log4.xml
	inclua algo como:
	<appender name="rollingFileAppenderOnlyEclipseLink" class="org.apache.log4j.RollingFileAppender"> 
		<param name="file" value="${log.path}/oauth-EclipseLink-${weblogic.Name}.log" /> 
		<param name="MaxFileSize" value="30MB" /> 
		<param name="MaxBackupIndex" value="50" /> 
		<param name="encoding" value="UTF-8" /> 
		<param name="datePattern" value="'.'yyyy-MM-dd"/> 
		<param name="append" value="true" /> 
		<layout class="org.apache.log4j.PatternLayout"> 
			<param name="ConversionPattern" value="[%d{dd/MM/yyyy HH:mm:ss,SSS}] EclipseLink %p%n %m%n%n" /> 
		</layout> 
	</appender> 
	
	<logger name="org.eclipse.persistence" additivity="false"> 
		<level value="INFO" /> 
		<appender-ref ref="console" />
		<appender-ref ref="rollingFileAppenderOnlyEclipseLink" /> 
	</logger> 