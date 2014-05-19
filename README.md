# Consul CLB for Go

randomly selects a `SRV` record answer, then resolves its `A` record to an ip, and returns an `Address` structure:

	type Address struct {
		Address string
		Port string
	}


example:
	
	svcName := "my-svc"

	srvRecord := svcName + ".service.consul"
	address, err := clb.LookupAddress(srvRecord)
	if err != nil {
		panic(err)
	}

	fmt.Print(address.Address + ":" + address.Port)

