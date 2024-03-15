<template>

<div class="flex justify-center items-center bg-blue-200 dark:bg-red-200 rounded-3xl shadow-xl mt-20"  :id="contactId">

	<div class="container mx-auto">

		<div class="w-full p-8 my-4 md:px-12 ">
			<div class="flex">
				<h1 class="justify-center text-3xl mx-auto py-10">Leave me a message</h1>
			</div>
			<div class="grid grid-cols-1 gap-5 md:grid-cols-2 my-5">
				<input class="w-full bg-gray-200 text-gray-900 mt-2 p-3 rounded-lg"
            type="text" placeholder="First Name*" />
				<input class="w-full bg-gray-200 text-gray-900 mt-2 p-3 rounded-lg"
            type="text" placeholder="Last Name*" />
				<input class="w-full bg-gray-200 text-gray-900 mt-2 p-3 rounded-lg"
            type="email" placeholder="Email*" />
				<input class="w-full bg-gray-200 text-gray-900 mt-2 p-3 rounded-lg"
            type="number" placeholder="Phone*" />
       		</div>
				<div class="mb-5">
					<textarea placeholder="Message*" class="w-full h-32 bg-gray-200 text-gray-900 mt-2 p-3 rounded-lg  focus:shadow-outline"></textarea>
				</div>
				<div class="my-2 w-1/2 lg:w-1/4">
					<button class="uppercase bg-gradient-to-r from-blue-400 to-blue-600 dark:from-red-400 dark:to-red-600 text-sm font-bold tracking-wide p-3 text-white rounded-full w-full">Send Message</button>
				</div>
			</div>

			
    </div>

</div>



</template>