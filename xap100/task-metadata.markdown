---
layout: post100
title:  Metadata
categories: XAP100
parent: task-execution-overview.html
weight: 400
---

{%summary%}{%endsummary%}


# Task Execution

{: .table .table-bordered}
|Attribute Annotation|@TaskGigaSpace   |
|Description         | This annotation injects a clustered proxy into the Task implementation. This is useful when the Task should access other partitions.   |

Example:

{%highlight java%}
public class MyTask implements Task<Integer>  {

    @TaskGigaSpace
    private transient GigaSpace colocatedSpace;
    private transient GigaSpace clusteredSpace;

    public MyTask() {
    }
....
}
{%endhighlight%}


{%learn%}./task-execution-overview.html{%endlearn%}


# Task Routing

{: .table .table-bordered}
|Method Annotation|@SpaceRouting  |
|Description         | This annotation selects the routing value. In case it is a POJO defined with a @SpaceRouting on one of its properties, the value of that property will be used as the routing information when passed as a parameter.   |


Example:

{%highlight java%}
public class MyTask implements Task<Integer>  {

    @SpaceRouting
    public Integer routing() {
       return this.value;
    }
....
}
{%endhighlight%}

{%learn%}./task-execution-overview.html{%endlearn%}