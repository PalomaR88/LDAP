Vagrant.configure("2") do |config|

  config.vm.define :postgres do |postgres|
    postgres.vm.box = "debian/buster64"
    postgres.vm.hostname = "servidor"
    postgres.vm.network :public_network,:bridge=>"enp2s0"
    #postgres.vm.network :public_network,:bridge=>"wlp1s0"
  end
end
