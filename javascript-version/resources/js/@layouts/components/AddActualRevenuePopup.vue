<template>
    <div class="popup">
        <div class="popup-inner">
            <button class="close-popup" @click="togglePopup">
                <box-icon name='x'></box-icon>
            </button>
            
            <div class="popup-content">
                <h1>Add Actual Revenue</h1>
                <form>
                    <div class="row">
                        <div class="form-group">
                            <label>ID</label>
                            <input type="text" v-model="formData.id" disabled />
                        </div>
                    
                        <div class="form-group">
                            <label>Accounting Period</label>
                            <input type="date" v-model="formData.accountingPeriod" />
                        </div>
                    
                        <div class="form-group">
                            <label>Status</label>
                            <select v-model="formData.status">
                                <option>Active</option>
                                <option>Inactive</option>
                            </select>
                        </div>
                    </div>
                    

                    <div class="row">
                        <div class="form-group">
                            <label>Client</label>
                            <select v-model="formData.client">
                                <option>GET</option>
                            </select>
                        </div>
                    
                        <div class="form-group">
                            <label>Deployment Area</label>
                            <select v-model="formData.deploymentArea">
                                <option>TBD</option>
                            </select>
                        </div>
                    
                        <div class="form-group">
                            <label>Product</label>
                            <select v-model="formData.product">
                                <option>Transit Ads</option>
                            </select>
                        </div>
                    </div>
                    
                    <div class="row">
                        <div class="form-group">
                            <label>Amount</label>
                            <input type="number" v-model="formData.amount" />
                        </div>
                    
                        <div class="form-group">
                            <label>Notes</label>
                            <input type="text" v-model="formData.notes" />
                        </div>
                    </div>
                    
                    
                    <button type="button" @click="saveData">Save</button>
                </form>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['togglePopup'],
    data() {
        return {
            formData: {
                id: 0,
                accountingPeriod: '',
                status: 'Active',
                client: '',
                deploymentArea: 'TBD',
                product: 'Transit Ads',
                amount: 0,
                notes: ''
            }
        };
    },
    methods: {
        saveData() {
            this.togglePopup();
        }
    }
}
</script>

<style lang="scss" scoped>
.popup {
    position: fixed;
    top: 0;
    left: 0;
    right: 0;
    bottom: 0;
    z-index: 99;
    background-color: rgba(0, 0, 0, 0.2);
    display: flex;
    align-items: center;
    justify-content: center;
}

.popup-inner {
    background: #FFF;
    padding: 32px;
    position: relative;
    width: 100%; 
    max-width: 1200px;
}

.close-popup {
    position: absolute;
    top: 10px;
    right: 10px;
    background: none;
    border: none;
    cursor: pointer;
}

.popup-content {
    max-width: 100%;
}

.row {
    display: flex;
    gap: 20px;
    margin-bottom: 15px;
}

.form-group {
    margin-bottom: 15px;
    width: 33%;
}

label {
    display: block;
    margin-bottom: 5px;
}

input, select {
    width: 100%;
    padding: 8px;
    box-sizing: border-box;
    border: 1px solid black;
}

input:disabled {
    background-color: #e9ecef;
    color: #6c757d;
    cursor: not-allowed;
}

button {
    display: block;
    margin-top: 20px;
    padding: 10px 20px;
    background-color: #007BFF;
    color: #FFF;
    border: none;
    cursor: pointer;
}
</style>
