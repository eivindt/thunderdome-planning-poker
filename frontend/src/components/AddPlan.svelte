<script>
    import SolidButton from './SolidButton.svelte'
    import CloseIcon from './icons/CloseIcon.svelte'

    export let handlePlanAdd = () => {}
    export let toggleAddPlan = () => {}
    export let handlePlanRevision = () => {}

    export let planId = ''
    export let planName = ''

    function handleSubmit(event) {
        event.preventDefault()

        if (planId === '') {
            handlePlanAdd(planName)
        } else {
            handlePlanRevision({
                planId,
                planName,
            })
        }
        toggleAddPlan()
    }
</script>

<div class="fixed inset-0 flex items-center z-40">
    <div class="fixed inset-0 bg-gray-900 opacity-75"></div>

    <div
        class="relative mx-4 md:mx-auto w-full md:w-2/3 lg:w-3/5 xl:w-1/3 z-50
        m-8">
        <div class="shadow-xl bg-white rounded-lg p-4 xl:p-6">
            <div class="flex justify-end mb-2">
                <button
                    aria-label="close"
                    on:click="{toggleAddPlan}"
                    class="text-gray-800">
                    <CloseIcon />
                </button>
            </div>

            <form on:submit="{handleSubmit}" name="addPlan">
                <div class="mb-4">
                    <label class="block text-sm font-bold mb-2" for="planName">
                        Plan Name
                    </label>
                    <input
                        class="bg-gray-200 border-gray-200 border-2
                        appearance-none rounded w-full py-2 px-3 text-gray-700
                        leading-tight focus:outline-none focus:bg-white
                        focus:border-purple-500"
                        id="planName"
                        type="text"
                        bind:value="{planName}"
                        placeholder="Enter a plan name"
                        name="planName" />
                </div>
                <div class="text-right">
                    <div>
                        <SolidButton type="submit">Save</SolidButton>
                    </div>
                </div>
            </form>
        </div>
    </div>
</div>
