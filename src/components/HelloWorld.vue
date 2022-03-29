<script>
    export default {
    data() {
        return {
        salary: undefined,
        grossIncome: self.salary,
        isData: true,
        purchasePrice: undefined,
        salsacSalary: undefined,
        }
    },
    methods: {
        calculateGross(x) {
            if (x > 0 && x <= 18200) {
                return Math.round(x)
            } else if (x >= 18201 && x <= 45000) {
                let tax = (x - 18200) * 0.19
                return Math.round(x - tax)
            } else if (x >= 45001 && x <= 120000) {
                let tax = (x - 45000) * 0.325
                return Math.round(x - tax - 5092)
            } else if (x >= 120001 && x <= 180000) {
                let tax = (x - 120000) * 0.37
                return Math.round(x - tax - 29467)
            } else if (x >= 180001) {
                let tax = (x - 180000) * 0.45
                return Math.round(x - tax - 51667)
            }
        },
        calculatePurchasePrice(x) {
          const newSalary = self.salary - self.purchasePrice
          return newSalary
        }
    }
    }
</script>

<template>
  <div class="container px-3">
      <div class="form-group">
        <label id="formHeadings">Salary Calculator</label>
        <br/>
        <input type="text" class="form-control" id="" aria-describedby="salary" v-model="salary" placeholder="Enter your salary...">
        <small id="helpId" class="form-text text-muted">Your information is secured with 256-bit encryption.</small>
      </div>
    <br/>

    <div class="row gx-4">
      <div class="col">
        <label id="formDescriptions">Gross Income</label>
        <label v-if='salary' class="form-control bg-light">{{ salary }}</label>
        <label v-else class="form-control bg-light">$0</label>
      </div>
      <div class="col">
        <label id="formDescriptions">Net Income</label>
        <label v-if='salary' class="form-control bg-light">${{ Math.floor(calculateGross(salary)) }}</label>
        <label v-else class="form-control bg-light">$0</label>
      </div>
    </div>

    <br/>

    <div class="row gx-4">
      <div class="col">
        <label id="formDescriptions">Net Monthly Income</label>
        <label v-if='salary' class="form-control bg-light">${{ Math.floor(calculateGross(salary) / 12) }}</label>
        <label v-else class="form-control bg-light">$0</label>
      </div>
      <div class="col">
        <label id="formDescriptions">Net Weekly Income</label>
        <label v-if='salary' class="form-control bg-light">${{ Math.floor(calculateGross(salary) / 52) }}</label>
        <label v-else class="form-control bg-light">$0</label>
      </div>
    </div>

    <br/><br/><br/>

    <div class="form-group">
      <label id="formHeadings">Salary Sacrifice Calculator</label>
        <br/>
        <input type="text" class="form-control" id="" aria-describedby="purchasePrice" v-model="purchasePrice" v-if=salary placeholder="Enter item purchase price...">
        <input type="text" class="form-control" id="" aria-describedby="purchasePrice" v-model="purchasePrice" v-else placeholder="Please enter your salary first" disabled>
        <small id="helpId" class="form-text text-muted">Can you afford this?</small>
      </div>
    <br/>
    
    <div class="row gx-4">
      <div class="col">
        <label id="formDescriptions">Pre-Tax Purchase Price</label>
        <label v-if="!purchasePrice" class="form-control bg-light">$0</label>
        <label v-else class="form-control bg-light">${{ (calculateGross(salary)) - (calculateGross(salary - purchasePrice)) }}</label>
      </div>
      <!-- 
      <div class="col">
        <label id="formDescriptions"></label>
        <label class="form-control bg-light">{{ weeklySalary }}</label>
      </div>
      -->
    </div>

    <br/>

  </div>
  

</template>

<style scoped>

.form-control {
  height: 50px;
  text-align: center;
}

#formDescriptions {
  color: white;
}

#formHeadings {
  color: white;
  font-size: x-large;
}

</style>
