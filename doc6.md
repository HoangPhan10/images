<h1>Ensure Os Login Is Enabled for a Project</h1>
Description: Việc bật osLogin đảm bảo rằng các khóa SSH dùng để kết nối tới các phiên bản máy chủ được ánh xạ với người dùng IAM. Khi thu hồi quyền truy cập của một người dùng IAM, toàn bộ các khóa SSH liên kết với người dùng đó cũng sẽ bị thu hồi. 
Solution: Cơ chế này hỗ trợ quản lý cặp khóa SSH một cách tập trung và tự động, rất hữu ích trong các tình huống như phản ứng với việc khóa SSH bị xâm phạm hoặc thu hồi quyền truy cập của người dùng bên ngoài, bên thứ ba hoặc nhà cung cấp.

Prowler Scan:
prowler gcp --check compute_project_os_login_enabled
image6.1
image6.2

Fix:
Terraform:
    resource 'google_compute_project_metadata' 'default' {
	..
	metadata = {
		enable-oslogin = true
	}
	..
    }
Command line:
    gcloud compute project-info add-metadata --metadata enable-oslogin=TRUE

Result:
image 6.3