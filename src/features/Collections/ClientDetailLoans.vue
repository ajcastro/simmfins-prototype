<template>
  <div class="q-mb-lg">
    <!-- <div class="col q-mt-md text-h6">Loans</div> -->
    <div class="row q-my-md text-subtitle1 text-bold text-grey">
      <div class="col">LOANS</div>
      <div class="col text-right">
        <q-badge class="text-caption text-bold q-mt-xs" color="info">{{ 2101.00 | currency('') }}</q-badge>
      </div>
    </div>

    <div class="row q-mt-md">
      <q-list bordered class="col loan-payment-details">
        <q-item>
          <q-item-section side @click.prevent="openLoanDialog = true">
            <q-icon name="info" color="primary" size="25px" class="cursor-pointer"></q-icon>
          </q-item-section>
          <q-item-section class="cursor-pointer" @click.prevent="openOffsettingDialog = true">
            <q-item-label class="text-subtitle1 text-bold">PLPEL-01234</q-item-label>
            <q-item-label class="text-subtitle1">
              2,101.00
              <span class="text-grey">●</span>
              30/20
            </q-item-label>
          </q-item-section>

          <q-item-section side>
            <div class="q-mr-sm">
              <q-popup-edit v-model="totalPayment" buttons>
                <q-input
                  type="number"
                  v-model="totalPayment"
                  input-class="text-bold"
                  @focus="$event.target.select()"
                  label="Amount Paid"
                  dense
                  autofocus
                />
              </q-popup-edit>
              <q-item-label class="text-h6 text-primary">{{totalPayment | currency('')}}</q-item-label>
            </div>
          </q-item-section>
        </q-item>

        <q-separator/>
      </q-list>
    </div>

    <!-- Loan info -->
    <q-dialog
      v-model="openLoanDialog"
      :maximized="true"
      transition-show="slide-up"
      transition-hide="slide-down"
    >
      <q-layout class="bg-white">
        <q-toolbar class="bg-primary text-white">
          <q-toolbar-title>Loan Information</q-toolbar-title>

          <q-btn flat round dense icon="fas fa-times" size="10px" @click="openLoanDialog = false"/>
        </q-toolbar>
        <q-card flat>
          <q-card-section>
            <q-item class="q-pa-none">
              <q-item-section side>
                <q-avatar size="48px">
                  <img src="https://cdn.quasar-framework.org/img/avatar6.jpg">
                </q-avatar>
              </q-item-section>
              <q-item-section>
                <q-item-label class="text-subtitle2">Marias Juana Dela Cruz</q-item-label>
                <q-item-label class="text-h6 text-bold">PLPEL-01234
                  <!-- <q-icon name="info" color="primary" @click="sho"></q-icon> -->
                </q-item-label>
                <q-item-label class="text-h6">
                  2,101.00
                  <span class="text-grey">●</span> 2,101.00
                </q-item-label>
              </q-item-section>
            </q-item>
            <q-separator class="q-mt-sm"/>
          </q-card-section>
          <q-card-section>
            <q-list>
              <q-item-label header class="q-pa-none text-bold">BALANCES</q-item-label>
              <q-item>
                <q-item-section>
                  <q-item-label class="text-grey text-bold">Principal</q-item-label>
                  <q-item-label class="text-subtitle2">
                    {{ 1000 | currency('') }}
                    <i class="text-grey">of</i>
                    {{ 10000 | currency('') }}
                  </q-item-label>
                </q-item-section>
              </q-item>

              <q-separator inset></q-separator>

              <q-item>
                <q-item-section>
                  <q-item-label class="text-grey text-bold">Interest</q-item-label>
                  <q-item-label class="text-subtitle2">
                    {{ 100 | currency('') }}
                    <i class="text-grey">of</i>
                    {{ 1000 | currency('') }}
                  </q-item-label>
                </q-item-section>
              </q-item>

              <q-separator inset></q-separator>

              <q-item>
                <q-item-section>
                  <q-item-label class="text-grey text-bold">Total</q-item-label>
                  <q-item-label class="text-subtitle2">
                    {{ 1100 | currency('') }}
                    <i class="text-grey">of</i>
                    {{ 11000 | currency('') }}
                  </q-item-label>
                </q-item-section>
              </q-item>

              <span class="q-mt-md"></span>

              <q-item-label header class="q-pa-none text-bold">PAYMENTS</q-item-label>
              <q-item>
                <q-item-section>
                  <q-item-label class="text-grey text-bold">Current Due</q-item-label>
                  <q-item-label class="text-subtitle2">
                    {{ 1000 | currency('') }}
                    <i class="text-grey">of</i>
                    {{ 1000 | currency('') }}
                  </q-item-label>
                </q-item-section>
              </q-item>

              <q-separator inset></q-separator>

              <q-item>
                <q-item-section>
                  <q-item-label class="text-grey text-bold">Past Due</q-item-label>
                  <q-item-label class="text-subtitle2">
                    {{ 1000 | currency('') }}
                    <i class="text-grey">of</i>
                    {{ 1000 | currency('') }}
                  </q-item-label>
                </q-item-section>
              </q-item>

              <q-separator inset></q-separator>

              <q-item>
                <q-item-section>
                  <q-item-label class="text-grey text-bold">Penalty Due</q-item-label>
                  <q-item-label class="text-subtitle2">
                    {{ 10 | currency('') }}
                    <i class="text-grey">of</i>
                    {{ 10 | currency('') }}
                  </q-item-label>
                </q-item-section>
              </q-item>

              <q-separator inset></q-separator>

              <q-item>
                <q-item-section>
                  <q-item-label class="text-grey text-bold">Advance</q-item-label>
                  <q-item-label class="text-subtitle2">{{ 1000 | currency('') }}</q-item-label>
                </q-item-section>
              </q-item>

              <q-separator inset></q-separator>

              <q-item>
                <q-item-section>
                  <q-item-label class="text-grey text-bold">Subsidized</q-item-label>
                  <q-item-label class="text-subtitle2">{{ 'NO' }}</q-item-label>
                </q-item-section>
              </q-item>
            </q-list>
          </q-card-section>
        </q-card>
      </q-layout>
    </q-dialog>

    <!-- dialog for offsetting -->
    <q-dialog
      v-model="openOffsettingDialog"
      :maximized="true"
      transition-show="slide-up"
      transition-hide="slide-down"
    >
      <q-layout class="bg-white">
        <q-toolbar class="bg-primary text-white">
          <q-toolbar-title>Payment Offsetting</q-toolbar-title>

          <q-btn
            flat
            round
            dense
            icon="fas fa-times"
            size="10px"
            @click="openOffsettingDialog = false"
          />
        </q-toolbar>
        <q-card flat>
          <q-card-section>
            <q-item class="q-pa-none">
              <q-item-section side>
                <q-avatar size="48px">
                  <img src="https://cdn.quasar-framework.org/img/avatar6.jpg">
                </q-avatar>
              </q-item-section>
              <q-item-section>
                <q-item-label class="text-subtitle2">Marias Juana Dela Cruz</q-item-label>
                <q-item-label class="text-h6 text-bold">PLPEL-01234
                  <!-- <q-icon name="info" color="primary" @click="sho"></q-icon> -->
                </q-item-label>
                <q-item-label class="text-h6">
                  2,101.00
                  <span class="text-grey">●</span> 2,101.00
                </q-item-label>
              </q-item-section>
            </q-item>
            <q-separator class="q-mt-sm"/>
          </q-card-section>
          <q-card-section>
            <q-card class="my-card">
              <q-card-section class="q-pa-none">
                <q-list>
                  <q-item>
                    <q-item-section>
                      <q-item-label class="text-subtitle1 text-bold">Cash
                        <q-toggle
                          v-model="subsidized"
                          dense
                          label="Subsidized?"
                          class="text-grey q-pa-none"
                        />
                      </q-item-label>
                    </q-item-section>

                    <q-item-section side>
                      <q-item-label class="row text-subtitle1">
                        <div>
                          <q-popup-edit v-model="totalPayment" buttons>
                            <q-input
                              type="number"
                              v-model="totalPayment"
                              input-class="text-bold"
                              @focus="$event.target.select()"
                              label="Amount Paid"
                              dense
                              autofocus
                            />
                          </q-popup-edit>
                          <q-item-label class="text-primary">{{totalPayment | currency('')}}</q-item-label>
                        </div>
                      </q-item-label>
                    </q-item-section>
                  </q-item>
                  <q-separator></q-separator>
                  <q-item>
                    <q-item-section>
                      <q-item-label class="text-subtitle1 text-bold">CBU</q-item-label>
                      <q-item-label class="text-subtitle1">5,00.00</q-item-label>
                    </q-item-section>

                    <q-item-section side>
                      <q-item-label class="text-subtitle1">
                        <div>
                          <q-popup-edit v-model="totalPayment" buttons>
                            <q-input
                              type="number"
                              v-model="totalPayment"
                              input-class="text-bold"
                              @focus="$event.target.select()"
                              label="Amount Paid"
                              dense
                              autofocus
                            />
                          </q-popup-edit>
                          <q-item-label class="text-primary">{{totalPayment | currency('')}}</q-item-label>
                        </div>
                      </q-item-label>
                    </q-item-section>
                  </q-item>
                  <q-separator></q-separator>
                  <q-item>
                    <q-item-section>
                      <q-item-label class="text-subtitle1 text-bold">Payment Thru MBA</q-item-label>
                    </q-item-section>

                    <q-item-section side>
                      <q-item-label class="text-subtitle1">
                        <div>
                          <q-popup-edit v-model="totalPayment" buttons>
                            <q-input
                              type="number"
                              v-model="totalPayment"
                              input-class="text-bold"
                              @focus="$event.target.select()"
                              label="Amount Paid"
                              dense
                              autofocus
                            />
                          </q-popup-edit>
                          <q-item-label class="text-primary">{{totalPayment | currency('')}}</q-item-label>
                        </div>
                      </q-item-label>
                    </q-item-section>
                  </q-item>
                  <q-separator></q-separator>
                  <!-- <q-item>
                    <q-item-section>
                      <q-item-label class="text-subtitle1 text-bold">Subsidized?</q-item-label>
                    </q-item-section>

                    <q-item-section side>
                      <q-item-label class="text-subtitle1">
                        
                      </q-item-label>
                    </q-item-section>
                  </q-item>-->
                  <!-- <q-separator></q-separator> -->
                </q-list>
              </q-card-section>
            </q-card>
          </q-card-section>
        </q-card>
      </q-layout>
    </q-dialog>
  </div>
</template>

<script>
export default {
  name: "Loans",
  data() {
    return {
      openLoanDialog: false,
      openOffsettingDialog: false,
      totalPayment: 2101.0,
      totalPayment2: 0,
      cash: 1101.0,
      cash2: 0.0,
      cbu: 1000.0,
      cbu2: 0.0,
      subsidized: false
    };
  },
  computed: {}
};
</script>

<style>
.q-list.loan-payment-details
  .q-expansion-item
  .q-expansion-item__container
  .q-item {
  padding: 0px;
}

#payments-table td,
#payments-table thead th {
  font-size: 1rem;
}
</style>
