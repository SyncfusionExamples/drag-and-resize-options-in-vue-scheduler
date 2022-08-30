<template>
    <ejs-schedule height="600px" :selectedDate='schedulerSelectedDate' 
      :eventSettings="appointmentData" allowMultiDrag='true'
      :allowDragAndDrop="draganddropOption" :allowResizing="resizingOption"
      :dragStart='onDragStart' :resizeStart='onResizeStart'>
    </ejs-schedule>
</template>

<script> 
import { ScheduleComponent, Day, Week, WorkWeek, Month, Agenda, DragAndDrop, Resize} from "@syncfusion/ej2-vue-schedule";

export default {
  name: 'App',
  components: { 'ejs-schedule': ScheduleComponent },
  provide : { schedule : [Day, Week, WorkWeek, Month, Agenda, DragAndDrop, Resize ] },
  methods : {
    onDragStart : function(args) {
      args.excludeSelectors = 'e-header-cells,e-all-day-cells';
      args.navigation.enable = true;
    //  args.interval = 10;
      args.interval = 1;
      args.scroll = { 
        enable : true, 
        scrollBy : 5,
        timeDelay : 100
      };
    },
    onResizeStart : function(args) {
     // args.interval = 10;
      args.interval = 1;
      args.scroll = { 
        enable : true,
        scrollBy : 5,
        timeDelay : 100 
      };
    }
  },
  data() {
    return {
      draganddropOption : true,
      resizingOption : true,
      schedulerSelectedDate : new Date(2022, 5, 6),
      appointmentData : {
         dataSource : [
             {
              Id : 1,
              Subject : 'Scrum Meeting',
              StartTime: new Date(2022, 5, 6, 9, 0, 0),
              EndTime: new Date(2022, 5, 6, 10, 0, 0)
            },
            {
              Id : 2,
              Subject : 'Demo Meeting',
              StartTime: new Date(2022, 5, 8, 10, 30, 0),
              EndTime: new Date(2022, 5, 8, 11, 30, 0)
            },
            {
              Id : 3,
              Subject : 'Core Team Meeting',
              StartTime: new Date(2022, 5, 7, 13, 0, 0),
              EndTime: new Date(2022, 5, 7, 14, 0, 0)
            },
            {
              Id : 4,
              Subject : 'Project Discussion',
              StartTime: new Date(2022, 5, 10, 14, 0, 0),
              EndTime: new Date(2022, 5, 10, 15, 0, 0)
            },
            {
              Id : 5,
              Subject : 'Testing',
              StartTime: new Date(2022, 5, 9, 12, 0, 0),
              EndTime: new Date(2022, 5, 9, 13, 0, 0)
            }
         ]
      }
    };
  }
}
</script>

<style>
  @import '../node_modules/@syncfusion/ej2-base/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-buttons/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-calendars/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-dropdowns/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-inputs/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-navigations/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-popups/styles/material.css';
  @import '../node_modules/@syncfusion/ej2-vue-schedule/styles/material.css';
</style>
