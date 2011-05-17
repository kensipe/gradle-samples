#Warning... Experimentation
This is largely a bunch of experiments... and some of this will move to the actual gradle code base.  There 2 useful tasks to play with: taskDag and depGraph

#taskDag 
generates the DOT notation for a task dag... so add plugins and tasks all you want then run taskDag.  It currently goes to STDIO... so copy the output from the console to a .gv file, and open from the console on a mac with "open task-dag.gv".  with omnigraffle present it will provide opening options.

sample output:
gradle tD
:taskDag
<code>
digraph dag {
  assemble -> jar
  build -> assemble
  build -> check
  buildDependents -> build
  buildNeeded -> build
  check -> test
  classes -> compileJava
  classes -> processResources
  classes -> task5
  task0 -> task2
  task0 -> task3
  task0 -> task5
  task1 -> task2
  task2 -> task3
  task3 -> task5
  task4 -> task0
  testClasses -> processTestResources
  testClasses -> compileTestJava
}
</code>
copy all details from the digraph to the closing } and save in a file with the "gv" extension.

#depGraph 
generates the DOT notation for a dependency graph...

sample output:
<code>
digraph dependencies { 
  org_springframework_spring_beans_3_0_5_RELEASE -> commons_logging_commons_logging_1_1_1
  org_springframework_spring_webmvc_3_0_5_RELEASE -> org_springframework_spring_beans_3_0_5_RELEASE
  org_springframework_spring_expression_3_0_5_RELEASE -> org_springframework_spring_asm_3_0_5_RELEASE
  org_springframework_spring_webmvc_3_0_5_RELEASE -> org_springframework_spring_core_3_0_5_RELEASE
  org_springframework_spring_context_3_0_5_RELEASE -> commons_logging_commons_logging_1_1_1
  org_springframework_spring_aop_3_0_5_RELEASE -> commons_logging_commons_logging_1_1_1
  org_springframework_spring_context_3_0_5_RELEASE -> aopalliance_aopalliance_1_0
  org_springframework_spring_webmvc_3_0_5_RELEASE -> org_springframework_spring_aop_3_0_5_RELEASE
  org_springframework_spring_webmvc_3_0_5_RELEASE -> org_springframework_spring_expression_3_0_5_RELEASE
  org_springframework_spring_context_3_0_5_RELEASE -> org_springframework_spring_asm_3_0_5_RELEASE
  org_springframework_spring_context_3_0_5_RELEASE -> org_springframework_spring_core_3_0_5_RELEASE
  org_springframework_spring_webmvc_3_0_5_RELEASE -> aopalliance_aopalliance_1_0
  org_springframework_spring_beans_3_0_5_RELEASE -> org_springframework_spring_asm_3_0_5_RELEASE
  project_dot_report -> org_springframework_spring_test_3_0_5_RELEASE
  org_springframework_spring_expression_3_0_5_RELEASE -> commons_logging_commons_logging_1_1_1
  org_springframework_spring_webmvc_3_0_5_RELEASE -> commons_logging_commons_logging_1_1_1
  org_springframework_spring_aop_3_0_5_RELEASE -> org_springframework_spring_core_3_0_5_RELEASE
  org_springframework_spring_context_3_0_5_RELEASE -> org_springframework_spring_beans_3_0_5_RELEASE
  project_dot_report -> junit_junit_4_8_2
  org_springframework_spring_webmvc_3_0_5_RELEASE -> org_springframework_spring_asm_3_0_5_RELEASE
  org_springframework_spring_aop_3_0_5_RELEASE -> org_springframework_spring_asm_3_0_5_RELEASE
  project_dot_report -> org_springframework_spring_webmvc_3_0_5_RELEASE
  org_springframework_spring_webmvc_3_0_5_RELEASE -> org_springframework_spring_context_3_0_5_RELEASE
}
</code>