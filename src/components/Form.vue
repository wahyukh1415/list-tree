<template>
<div>
    <div id="multiselect-sample">
        <div class="col-lg-8 control-section">
            <div class="control-styles">
                <h4>CheckBox</h4>
                <ejs-multiselect id='multiselect-checkbox' :dataSource='countries' :placeholder='checkWaterMark' :fields='checkFields'
                    :mode='multiMode' :popupHeight='popHeight' :showDropDownIcon='showDropDownIcon' :showSelectAll='showSelectAll'
                    :enableSelectionOrder='enableSelectionOrder' :filterBarPlaceholder='filterPlaceholder'></ejs-multiselect>
            </div>
        </div>
        <div class="col-lg-4 property-section">
            <table id="property" class="property-panel-table" title="Properties">
                <tr>
                    <td style="width: 50%;">
                        <div>
                            <ejs-checkbox ref="checkboxInstance1" label="Show Select All" :checked="true" :change="onChange"></ejs-checkbox>
                        </div>
                    </td>
                </tr>
                <tr>
                    <td style="width: 50%;">
                        <div>
                            <ejs-checkbox ref="checkboxInstance2" label="Dropdown Button" :checked="true" :change="onChangeDrop"></ejs-checkbox>
                        </div>
                    </td>
                </tr>
                <tr>
                    <td style="width: 50%;">
                        <div>
                            <ejs-checkbox ref="checkboxInstance3" label="Selection Reorder" :checked="true" :change="onChangeReorder"></ejs-checkbox>
                        </div>
                    </td>
                </tr>
            </table>
        </div>
    </div>
</div>
</template>
<style scoped>
    .control-styles {
        margin: 0 auto; 
        width:300px; 
        padding-top: 25px
    }
</style>
<script>
import Vue from "vue";
import { MultiSelectPlugin, CheckBoxSelection } from "@syncfusion/ej2-vue-dropdowns";
import { CheckBoxPlugin } from "@syncfusion/ej2-vue-buttons";
import * as data from './dataSource.json';

Vue.use(MultiSelectPlugin);
Vue.use(CheckBoxPlugin);

export default Vue.extend ({
    data: function() {
        return {
            checkFields: { text: 'Name', value: 'Code' },
            checkWaterMark: 'Select countries',
            popHeight: '350px',
            multiMode: 'CheckBox',
            filterPlaceholder: 'Search countries',
            showSelectAll: true,
            showDropDownIcon: true,
            enableSelectionOrder: true,
            countries:data['countries']
        };
    },
    methods: {
        onChange: function() {
            var checkboxObj = this.$refs.checkboxInstance1.ej2Instances;
            // enable or disable the select all in Multiselect based on CheckBox checked state
            this.showSelectAll = checkboxObj.checked;
        },
        onChangeDrop: function() {
            var dropdownObj = this.$refs.checkboxInstance2.ej2Instances;
            // enable or disable the dropdown button in Multiselect based on CheckBox checked state
            this.showDropDownIcon = dropdownObj.checked;
        },
        onChangeReorder: function() {
            var reorderObj = this.$refs.checkboxInstance3.ej2Instances;
            // enable or disable the list reorder in Multiselect based on CheckBox checked state
            this.enableSelectionOrder = reorderObj.checked;
        }
    },
    provide: {
        multiselect: [CheckBoxSelection]
    }
});
</script>