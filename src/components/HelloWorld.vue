<template>
  

  <!-- Add margin-top to the first section to account for fixed header -->
  <section id="home" class="pt-32 pb-20">
    <div class="container mx-auto px-4 flex flex-col md:flex-row items-center">
      <div class="md:w-1/2 mb-10 md:mb-0">
        <h1 class="text-4xl md:text-6xl font-bold text-gray-800 mb-4">Hi, I'm Brandon Johnson</h1>
        <h2 class="text-2xl md:text-3xl text-blue-600 mb-6">Web Developer</h2>
        <p class="text-gray-600 mb-8 text-lg">With 2 years of experience building web applications</p>
        <a href="#profile" class="bg-blue-600 text-white px-6 py-3 rounded-lg hover:bg-blue-700 transition"
          @click="smoothScroll">Learn More</a>
      </div>
    </div>
  </section>

  <!-- Rest of the sections remain the same, just update any personal information -->
  <section id="profile" class="py-16 bg-white rounded-lg shadow-md mb-10">
    <div class="container mx-auto px-4">
      <h2 class="text-3xl font-bold text-center mb-12 text-gray-800">My Profile</h2>
      <div class="max-w-3xl mx-auto bg-gray-50 p-8 rounded-lg">
        <div class="grid grid-cols-1 md:grid-cols-2 gap-8">
          <div>
            <h3 class="text-xl font-semibold mb-4 text-blue-600">Personal Information</h3>
            <ul class="space-y-3">
              <li class="flex items-start">
                <span class="text-gray-600 w-24">Name:</span>
                <span class="font-medium">Brandon Johnson</span>
              </li>
              <li class="flex items-start">
                <span class="text-gray-600 w-24">Phone:</span>
                <span class="font-medium">(123) 456-7890</span>
              </li>
              <li class="flex items-start">
                <span class="text-gray-600 w-24">Email:</span>
                <span class="font-medium">brandon.johnson@example.com</span>
              </li>
            </ul>
          </div>
          <div>
            <h3 class="text-xl font-semibold mb-4 text-blue-600">Professional Summary</h3>
            <p class="text-gray-700">
              Web developer with 2 years of experience in both frontend and backend development.
              Skilled in creating responsive web applications using modern frameworks and technologies.
            </p>
          </div>
        </div>
      </div>
    </div>
  </section>
 



  <!-- Rest of the template remains the same -->
</template>

<script>

export default {
  name: 'HelloWorld',
  components() {

  },
  
  // Methods remain the same
}
</script>