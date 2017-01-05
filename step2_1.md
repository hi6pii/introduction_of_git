# �ȉ����Q�Ƃ��āA���ɋL���Ɏc�������������R�s�y����
https://github.com/takanabe/introduction-to-git/blob/master/02_first_commit.md


### ���|�W�g���̍쐬
    $ git init

### �f�B���N�g���̊m�F
    $ ls -a


### ���݂̃��|�W�g���ƍ�ƃR�s�[�̏�Ԃ� Git ����͂ǂ��F�����Ă��邩
    $ git status
�uOn branch master�v �Ƃ���܂��ˁB�u�u�����` master �ゾ��v  
�uInitial commit�v �Ə�����Ă��܂��ˁB�u�ŏ��̃R�~�b�g����v�Ə�����Ă��܂�  
�uUntracked files:�v �B�u�g���b�N����Ă��Ȃ��t�@�C���͈ȉ��̂Ƃ��肾��Fnyan.txt�v  
�uuse "git add <file> ..." to include in what will be committed�v �Ə�����Ă��܂��B�u�R�~�b�g�������̂Ɋ܂߂������ "git add <file>..." �g���Ηǂ���v���Ă��Ƃł��ˁB  
�unothing added to commit but untracked files present (use "git add" to track)�v �Ə�����Ă��܂��ˁB�u�R�~�b�g������̂��Ȃɂ��Ȃ���A�ł��ǐՂ���ĂȂ��t�@�C���������(�ǐՂ�������� "git add" ����Ƃ�����)�v  


### stage��unstage

�u���ɃR�~�b�g����Ƃ��Ƀ��|�W�g���ɔ��f�������e�̒u����v�̂��Ƃ��A"staging area" �ƌĂ�ł��܂�
stage

    $ git add nyan.txt

unstage

    $ git rm --cached nyan.txt



### commit���Ă݂�

    $ git commit

���b�Z�[�W�������Ӗ�  
1. �u�������c���v�B�u�N���v�u���v�u�����������v���A�R�~�b�g���b�Z�[�W�Ƃ��Ďc���Ă����K�v������ -> �Q�ƁA�Č��A����
  1. �Č��F���삵�Ȃ��Ȃ���O�ɖ߂��Ƃ���蒼���Ƃ��������Ƃ�A�o�O���������鎞�_�̐��ʕ����A���̃����o�[�Ɋm�F���Ă��炤�A�Ƃ��������Ƃ��\�ɂȂ�܂�
  1. ����F���삵�Ȃ��Ȃ��O�̏�Ԃ����ɕʂ̕ύX�������Ă����A���ꂼ��̃p�^�[���������o�[�ɕ]�����Ă��炤�A�Ƃ��������Ƃ��ł���悤�ɂȂ�܂�
1. ��Ƃ̋�����h�� -> ����(merge)���\�ɂȂ�A���̃����o�[�ƌ����悭���s���č�Ƃ������߂���


### �������m�F

    $ git log


### �R�~�b�g�����Ɖ���������̂�

�R�~�b�g���ꂽ�Ƃ�A���|�W�g���ɂ͐V�����u�R�~�b�g�I�u�W�F�N�g�v�����܂��
�R�~�b�g�I�u�W�F�N�g�́ustaging����Ă����t�@�C���̓��e + �R�~�b�g���b�Z�[�W�v
���ꂼ��̃R�~�b�g�I�u�W�F�N�g�ɂ͈�ӂ�id�����Ă���


### stage���ꂽfile�̕ύX

    $ git status
    # Changes not staged for commit:
    #   (use "git add <file>..." to update what will be committed)
    #   (use "git checkout -- <file>..." to discard changes in working directory)
�u�R�~�b�g�p�� stage ����ĂȂ��ύX�͈ȉ��̒ʂ�ł��B�ύX���ꂽ�t�@�C���Fnyan.txt�v��ƃf�B���N�g���̓��e��ύX�������ǁA���̃t�@�C���̂��̓��e�� staging area �ɏオ���ĂȂ��킯�ł��ˁB  
�uuse "git checkout -- <file>..." to discard changes in working directory�v�������ł��B�u"git checkout -- <file> ..." ����ƁA��ƃf�B���N�g�����ł̕ύX���Ȃ��������Ƃɂł����I�v

    $ git add
    # Changes to be committed:
    #   (use "git reset HEAD <file>..." to unstage)
���ʂ̒��́uuse "git reset HEAD <file>..." to unstage�v�Ƃ���܂��B�u"git reset HEAD <file> ..." ���Ă���unstage�ł����v���Ă��Ƃł��ˁB

    $ git reset HEAD nyan.txt
    Unstaged changes after reset:
    M   nyan.txt
�uunstage���ꂽ�ύX�͈ȉ��̒ʂ肾��BM nyan.txt�v���Ă��Ƃł��ˁBM nyan.txt �͂Ȃ�ƂȂ��@�������Ă邩�Ǝv���܂����A�uModified�v�� M �ł��Bnyan.txt���ύX����Ă邯�ǁA���̕ύX�� git reset �ɂ���� unstage ���ꂽ����Č����Ă���Ă܂��ˁB


### �R�~�b�g�I�u�W�F�N�g�ӂ�����
    $ git commit
    1 file changed, 1 insertion(+), 1 deletion(-)
�u��̃t�@�C�����ύX����Ăā[�A��s�}������Ăā[�A��s�����Ă�I�v�Ƃ̂��Ƃł��A��s�ҏW������Ă̂͌���������Έ�s�����Ĉ�s�}��������Ă��ƂȂ̂ŁA�Ȃ�قǂˁI���Ċ����ł��ˁB

�厖�Ȃ̂́F
- �R�~�b�g�ɂ͐e�q�֌W������
- �R�~�b�g�I�u�W�F�N�g�ɂ́u�e�R�~�b�g�͂ǂꂩ�v�Ƃ������ƁA�u���̏u�Ԃ̃t�@�C���̏�ԁv�Ƃ�����񂪓����Ă���
- �����̂ӂ��̏����ׂ邱�Ƃɂ���āAGit ����͂��ł��u���� 2 �̃R�~�b�g�̊Ԃɂǂ̂悤�ȕύX���s��ꂽ���v��m�邱�Ƃ��ł���


    $ git log --graph  


git log �̕\���t�H�[�}�b�g�͂��낢�낢�����̂ŁA�C�ɂȂ�ЂƂ͒��ׂĂ݂āA�����̍D���ȃt�H�[�}�b�g�Ō��Ă݂�Ƃ����Ǝv���܂�


### �t�@�C���̍폜
    $ git rm filename
git rm �Ƃ����R�}���h�F
- ��ƃf�B���N�g���Ƀt�@�C�������݂���Ƃ��ɂ͂��̃t�@�C�����폜����(���łɖ����ꍇ�͂Ȃɂ����Ȃ�)
- ���̌�u�t�@�C�����폜������v�Ƃ������� stage ����


### �t�@�C���̃��l�[���A�ړ�
�u�t�@�C���̃��l�[���A�ړ��v�́A�����́u�V�����ꏊ(���O)�ɓ������e�̃t�@�C��������āA�Â��ꏊ�ɂ���t�@�C���������v�Ƃ�������ł���B
�Ȃ̂ŁA�t�@�C�������l�[��/�ړ� �����ꍇ�́A�u�V�����t�@�C�����ł�����v�Ƃ������� git add �� stage�A�u�Â��t�@�C���͏�������v�Ƃ������� git rm �� stage ���邱�ƂŃ��l�[��/�폜���\���ł���B

    $ git add �����l�[����̃t�@�C���̖��O��
    $ git rm �����l�[���O�̃t�@�C���̖��O��

���

      $�@git mv  �����l�[���O�̃t�@�C���̖��O�� �����l�[����̃t�@�C���̖��O��

���g���ƁA�u��ƃf�B���N�g�����̃t�@�C���̃��l�[��/�ړ��v�ƁA�u���̕ύX�� stage�v����C�ɂ���Ă����


### git �ɂ�����u�����`�͂����̃|�C���^�ł���
�u�����`�Ƃ����̂̓R�~�b�g�I�u�W�F�N�g���w������

    $ git branch

�ȉ�Tips:

    $ git log --graph --pretty=format:'%s %d'

git log --graph �� --pretty=format:'%s %d' �Ƃ����I�v�V������n���Ă݂܂����B����́A�R�~�b�g�̗����� '%s %d' �Ƃ����t�H�[�}�b�g�ŕ\�����ĂˁA�Ƃ����Ӗ��ł��B'%s' �̓R�~�b�g���b�Z�[�W�A'%d' ���u�����`���Ӗ����܂��B
���O�����ė������ׂ����Ƃ́umaster �Ƃ����u�����`�����݂��Ă��āA���� master �u�����`�� "�����t�@�C���� animals �f�B���N�g���Ɉړ�" �Ƃ����R�~�b�g�I�u�W�F�N�g���w���Ă���v�Ƃ������ƁB

    $ git log --graph --date-order --all --pretty=format:'%h %Cred%d %Cgreen%ad %Cblue%cn %Creset%s' --date=short

### �V�����u�����`�̍쐬
    $ git branch my_first_branch
my_first_branch �Ƃ����u�����`���o���Ă��āAmaster�Ɠ������ŐV�̃R�~�b�g�I�u�W�F�N�g���w���Ă���̂����Ď���Ƃ������܂��B

    $ git commit
�R�~�b�g���s����ƁA�R�~�b�g�I�u�W�F�N�g���쐬�����̂ł����ˁB�����āA���̃R�~�b�g�I�u�W�F�N�g�́A�u�e�R�~�b�g�I�u�W�F�N�g�͂ǂ�Ȃ̂��v�Ƃ������ƁA�u���̏u�Ԃ̃t�@�C���̏�ԁv�Ƃ������������Ă���̂ł����B�����ł��B���́A�u�e�R�~�b�g�I�u�W�F�N�g�v�ɂȂ�̂́A�u�R�~�b�g����Ƃ��ɑI������Ă����u�����`���w�������Ă���R�~�b�g�I�u�W�F�N�g�v�Ȃ̂ł��B�R�~�b�g���s����ƁAGit ����́u�I������Ă���u�����`���w�������Ă���R�~�b�g�I�u�W�F�N�g�v��e�Ƃ��āA�V�����R�~�b�g�I�u�W�F�N�g���쐬���܂��B���̌�AGit ����́u�I������Ă���u�����`�v�����̐V�����ł����R�~�b�g�I�u�W�F�N�g���w�������悤�ɍX�V���܂��B

���̃^�C�~���O�� HEAD �Ƃ������݂̂Ȃ��ɂ������Ă����܂��傤�B���͂��� HEAD �Ƃ����͓̂���ȃu�����`(�|�C���^)�ŁA�u���I�����Ă���u�����`���ǂ�Ȃ̂��v�Ƃ�������ێ����Ă���̂ł��B���AHEAD �� master �Ɠ����Ƃ���ɂ���܂��ˁB�܂�A���� master ���I������Ă���A�Ƃ������Ƃł��B


### �I�𒆂̃u�����`��؂�ւ��Ă݂�
    $ git checkout my_first_branch
����u�����`�� checkout ����ƁAGit ����͂ӂ��̂��Ƃ��s���܂��B
1. HEAD���w�肵���u�����`�ɐ؂�ւ���
2. ��ƃf�B���N�g���̓��e���A���̃u�����`���w�������R�~�b�g�̂Ƃ��̏�Ԃɕ�������
�������c���\�͂ɂ��ł���݂��̂��Ƃ̂����A�u�Q�Ɓv�Ɓu�����v�����ۂɍs���Ă݂܂����B�c��́u����v�ł��B


### �}�[�W����
    Merge made by the 'recursive' strategy.
     animals/mow.txt | 1 +
     1 file changed, 1 insertion(+)
     create mode 100644 animals/mow.txt

 �uMerge made by the 'recursive' strategy.�v �Ƃ���܂��ˁB�u'recursive' strategy �� merge ���ꂽ��v�������ł��B'recursive' starategy ���ĂȂɁc�c���Ċ����ł����A�ЂƂ܂����͂���͒u���Ă����܂��B�u�Ȃ�炩�̕��@�Ń}�[�W���ꂽ�񂾂ȁv�ƍ��͎v���Ă����Ă��������B

 ���̎��̍s�A�uanimals/mow.txt | 1 +�v�ƕ\������Ă��܂��B�Ȃ�ƂȂ��킩��ł��傤���B�uanimals/mow.txt�Ƃ����t�@�C����1�s�����Ă��v���炢�̊����ł��ˁB���̉��ɕ\������Ă�����e���A�����킩��܂��ˁB�u1�t�@�C���ύX�������āA1�s�ǉ�����Ă��v�ƁA�uanimals/mow.txt ���ăt�@�C�����������v�ł��ˁB�������ɁAmy_first_branch �ɂ͂��邯��� master �ɂ͂Ȃ��t�@�C���́A�u"mow" �� 1 �s�����ꂽ�����ꂽ animals/mow.txt�v�Ƃ����t�@�C���ł����B���̃t�@�C������荞�ނ̂�����A���̂悤�Ȍ��ʂɂȂ�͔̂[���ł��ˁB

1. `$ git merge branch_name`  �ŁA���I������Ă���u�����`�� branch_name �Ƃ������O�̃u�����`�̃R�~�b�g���e����荞�ނ��Ƃ��ł���
2. �}�[�W����Ƃ��ɂ́u�}�[�W�R�~�b�g�v�Ƃ�������ȃR�~�b�g���s���A�}�[�W�R�~�b�g�̃R�~�b�g�I�u�W�F�N�g�͐e���ӂ�����
3. ���̃}�[�W�R�~�b�g�����u���̏u�Ԃ̃t�@�C���̏�ԁv�́A�ӂ��̐e�������Ă������e�����킹�����̂ɂȂ�
4. `git branch -d branch_name` �Ƃ��邱�ƂŁAbranch_name �Ƃ������O�̃u�����`���������Ƃ��ł���


### �ҏW��Ƃ̓u�����`��
�ł͂�������A�ً}�̍�Ƃ̂��߂̃u�����`��؂��Ă����Ɉړ����܂��傤�B���O�� hotfix �ɂ��܂��傤���B���܂ł�

    $ git branch �u�����`��
    $ git checkout �u�����`��
�Ƃӂ��̃R�}���h��ł��Ă��܂������A�u�u�����`��؂��Ă����Ɉړ�����v�Ƃ����̂͂��͈ꔭ�łł���R�}���h������܂��B����͂�������g���܂��傤�B

    $ git checkout -b hotfix
����ŁA hotfix �Ƃ������O�̃u�����`���쐬���A���̃u�����`��I���������ƂɂȂ�܂��B

    $ git merge hotfix
    merge message:
    Fast-forward
     cat_hater_said.txt | 2 +-
     cat_lover_said.txt | 2 +-
     2 files changed, 2 insertions(+), 2 deletions(-)
���̃O���t�A��{���ŁA�u����v���Ă܂���ˁB���āA���̂Ƃ��Amaster �u�����`�� hotfix �u�����`�̕ύX���e����荞�����Ǝv�����ꍇ�A��Ԋy�ȕ��@�͂Ȃ�ł��傤���B�P���� master �u�����`�� hotfix �Ɠ����Ƃ�����w���悤�ɂ��Ă��܂��΁A����� master �u�����`�� hotfix �u�����`�̕ύX���e�𔽉f�����̂Ɠ������ƂɂȂ�܂��ˁB���������Ƃ��A���� Git ����́u���Ⴀ����ł������v�Ƃ��������ŒP���� master �̃u�����`�� hotfix �Ɠ����Ƃ���܂Ői�߂�̂ł��B�ŁA�������� merge �̎d�����uFast-forward�v�ƌĂ�ł���̂ł��B

fast-foward����ƃ��O���c��Ȃ��̂ł��ꂪ����ȏꍇ

    $ git merge --no-ff hotfix

�������邱�Ƃ� recusive strategy �Ń}�[�W�����
�Ƃ���ŁA����� Fast-fowarding �����Ƀ}�[�W�R�~�b�g���������Ń}�[�W���s���܂������AFast-foward �ł���Ƃ��� Fast-foward ���Ă��܂��ق����D�݂ł���Ƃ����ЂƂ����܂��B���̂�����͌��݂ł������ɏ@���푈���N�����Ă���̂ŁA���Ȃ��̏�������g�D��v���W�F�N�g�̂����ɍ��킹��Ƃ����ł��傤�B


### �}�[�W�@����
    $ git checkout master
    $ git merge unify_styles
    Auto-merging cat_lover_said.txt
    CONFLICT (content): Merge conflict in cat_lover_said.txt
    Auto-merging cat_hater_said.txt
    CONFLICT (content): Merge conflict in cat_hater_said.txt
    Automatic merge failed; fix conflicts and then commit the result.

�uAuto-merging cat_lover_said.txt�v�́ucat_lover_said.txt �� �����}�[�W���Ă��v�ł����ł��ˁB���̂��ƁA�uCONFLICT (content): Merge conflict in cat_lover_said.txt�v�ƌ����Ă��܂��B�I�b�A����́u�����v�ł��ˁB�悭�l���Ă݂�ƁAhotfix �ł� cat_lover_said.txt �̈�ԍŌ�̍s��ҏW���Ă��܂����Aunify_styles �ł���ԍŌ�̍s��ҏW���Ă��܂��Ă��܂��B���̂��߁AGit ����́u���A����ǂ����̏�Ԃ�^�Ƃ���΂����񂾁H�v�ƍ������Ă��܂��āA�����Ń}�[�W���s���Ȃ������킯�ł��ˁB�@�@

�����čŌ�ɁA�uAutomatic merge failed; fix conflicts and then commit the result.�v�Ə�����Ă��܂��ˁB�u�����}�[�W�Ɏ��s������������� �����𒼂��āA���̌��ʂ��R�~�b�g���ĂˁI�v�ƌ����Ă��܂��B����ꂽ�Ƃ���ɂ��܂��傤�B

�ƁA���̂܂��ɁA�Ȃɂ͂Ƃ����� status ���m�F�B

    $ git status
    # On branch master
    # You have unmerged paths.
    #   (fix conflicts and run "git commit")
    #
    # Unmerged paths:
    #   (use "git add <file>..." to mark resolution)
    #
    #   both modified:      cat_hater_said.txt
    #   both modified:      cat_lover_said.txt
    #
    no changes added to commit (use "git add" and/or "git commit -a")
�����������\���ł��ˁB

�u�}�[�W����ĂȂ��p�X�������(�R���t���N�g���C������ git commit ���Ă�)�B�v�������ł��B���́u�p�X�v���Ă̂́u�t�@�C���p�X�v�̂��Ƃł��ˁB�t�@�C���̂��Ƃ��Ǝv���Ă���Ă��܂��܂���B

���̉��ɂ́u�}�[�W����ĂȂ��p�X�͈ȉ��̒ʂ肾��(�C����������ă}�[�N�t���邽�߂ɂ� git add <file> ...���Ă�)�B
- �����ŕύX����Ă���t�@�C���Fcat_hater_said.txt
- �����ŕύX����Ă���t�@�C��:cat_lover_said.txt
�Ƃ���܂��ˁB

cat_hater_said.txt�����Ă݂��
�r����

    <<<<<<< HEAD
    �L�D���Ȑl�Ԃ�����̂��s�v�c�B
    =======
    >>>>>>> unify_styles
�̂悤�ȋL�ڂ�����B����́A�u�ǂ��������Ń}�[�W�ł��Ȃ��������v�� Git ���񂪋����Ă��ꂽ�̂ł��B
<<<< HEAD ���� ======�@�܂ł� HEAD�ŕҏW���ꂽ���e�ł��B�����HEAD��master�ł����ˁB  
��� ===== ����@>>>>> unify_styles�܂ł�unify_styles�ɏ�����Ă������e�B�ǂ����git ����́Aunify_styles�̂ق���
�ǂ��Ȃ�������ǂ����킩��Ȃ������݂����ł��ˁB

������蓮�ŉ������Ă��܂����B(�ł��}�[�W��̂��̂��Q�Ƃ������ꍇ�A�ǂ�������ǂ��̂ł��傤�H�H�j

git status �Ŋm�F���܂��B

    $ git status
    # On branch master
    # All conflicts fixed but you are still merging.
    #   (use "git commit" to conclude merge)
    #
    # Changes to be committed:
    #
    #   modified:   cat_hater_said.txt
    #   modified:   cat_lover_said.txt
    #
    ���A�\�����ς��܂����ˁB

�uAll conflicts fixed but you are still merging.(use "git commit" to conclude merge)�v�Ƃ���܂��ˁB���{��ɂ���΁u�����͑S�������������ǁA�܂��}�[�W������B(�}�[�W������������ɂ́Agit commit ���Ă�)�v�ł��B


### �}�[�W������ �܂Ƃ�
- �Ȃɂ���Ƃ��s���Ƃ��̓u�����`��؂��Ă���s���ƁA���ł��u���̍�Ƃ��s���O�̏�ԁv�ɖ߂��̂ŕ֗�
- �u����v���ĂȂ��u�����`���}�[�W����Ƃ��ɂ� Fast-foward �Ƃ�����@�������
- Fast-foward ���ƁA�}�[�W�R�~�b�g�͍��ꂸ�A����Ƀu�����`���i�߂���
    - Fast-foward �������Ȃ��Ƃ��ɂ� --no-ff �Ƃ����I�v�V������t����
- �}�[�W�����Ƃ��ɋ��������������ꍇ�ɂ́A�蓮�Ń}�[�W����
    - �t�@�C�����蓮�ŏC��
    - git add ���C�������t�@�C�����Ƃ��āu�����𒼂�����v�� Git �ɓ`����
    - �S���������� git commit �Ń}�[�W�R�~�b�g������������

### ��Ƃ̓g�s�b�N�u�����`��
�u����̖ړI�̍�Ƃ��s�����߂̃u�����`�v�̂��Ƃ��A�u�g�s�b�N�u�����`�v�Ƃ��u�t�B�[�`���[�u�����`�v�ƌĂԂ��Ƃ������ł��B����g�s�b�N�₠��@�\�ɓ��������u�����`�A���炢�̈Ӗ��ł��ˁB

### �g�s�b�N�u�����`�ō�Ƃ��ĊJ�A�������񂾂��ǁc�c
���͂��� unify_styles �u�����`�ł̍�Ƃ��n�߂��̂� hotfix ���s����O�ł������A���ɁA�������ꂪ�Ahotfix ���s��ꂽ���Ƃɔ��������^�X�N��������A�b�͂����Ԃ�V���v���ɂȂ�̂ɂȁA�Ǝv���܂��񂩁H

���Ⴀ�A���������ӂ��ɗ��j�����ς����Ⴆ�΂�����ł��B���ς����Ⴂ�܂��傤�B

    $ git checkout unify_styles
    $ git rebase master
    First, rewinding head to replay your work on top of it...
    Applying: under updating of files: tentative commit

�u�܂��Ahead �������߂���B����́A�N����������Ƃ��ŏ����烊�v���C���邽�߂���I�v�ƌ����Ă܂��ˁB�����āA���̂��ƂɁA�u�K�p���Funder updating of files: tentative commit�v�Ƃ���܂��B
rebase�ōs���Ă���̂�
1. unify_styles �̊e�R�~�b�g�Łu�ǂ̂悤�ȕύX���s�����̂��v���o���Ă���
1. master (hotfix �� merge �������Ƃ̏��) �� checkout����
1. ��������V�����܂� unify_styles�u�����`��؂�
1. �o���Ă������u�ǂ̂悤�ȕύX���s�����̂��v���C�`����K�p�������čs���B


### rebase�́A�������܂������킯�ł͂Ȃ�
���Ƃ��Έȉ��̂悤�ȃ��b�Z�[�W���łĂ���
    When you have resolved this problem, run "git rebase --continue".
    If you prefer to skip this patch, run "git rebase --skip" instead.
    To check out the original branch and stop rebasing, run "git rebase --abort".
    ��������������A"git rebase --continue".�����ĂˁB
    ���̕ύX���X�L�b�v�����Ⴂ�����Ȃ�A"git rebase --skip" ����B
    ���Ƃ̃u�����`�� checkout ���ă��x�[�X����߂Ă��܂������Ȃ�A"git rebase --abort" ���Ă�


### �u���O�̃R�~�b�g�����Ȃ����v�Ƃ������j���ϕ��@
    $ git commit --amend

### merge ���g���ׂ��Ȃ̂� rebase ���g���ׂ��Ȃ̂�

���āArebase ���g���ƃO���t�◚�����������肷��̂͂킩��܂����B�ł́A���������P�[�X�ł͂��ł� rebase ���g���ׂ��Ȃ̂ł��傤���H ��������\���݂ł��@���푈�������ɍs���Ă���g�s�b�N�Ȃ̂ŁA���Ȃ��̏�������g�D��v���W�F�N�g�̂����ɍ��킹��̂��ǂ��ł��傤�B

���Ȃ݂ɁA�M�҂͍ŋ߂ł� rebase �̂悤�ȑ�|����ȉߋ����ς́u�_�[�N�T�C�h�v�ł���Ƃ��������ɗ^������̂ł��Brebase����ƁAGit ���񂪏���ɉߋ��̃R�~�b�g�����������Ă��܂��܂��B����ɂ���āA�u�����Ɩ��Ȃ������Ă����R�~�b�g�v���u�����Ȃ��R�~�b�g�v�ɂȂ��Ă��܂��\��������A�Ƃ����̂����̗��R�ł��B

�������A�}�[�W�R�~�b�g�ł����̂悤�Ȃ��Ƃ͋N����̂ł����A�}�[�W�R�~�b�g�̏ꍇ�͂��̌�̃e�X�g�ł��Ȃ炸�����Ɂu�����Ȃ��R�~�b�g�v������Ă��܂������Ƃ��m�F�ł��܂����A���x�[�X�ŏo���オ�����R�~�b�g�����������ēx�e�X�g����̂͌����I�ł͂Ȃ��ł���ˁH


### �݂�ȂŎg��
�܂��͍���̃u�����`�̉^�p�̃|���V�[�����߂܂��傤�B

�܂��Amaster�u�����`�ł����Amaster �u�����`�ɃR�~�b�g������̂́u�����[�X������́v�����A�Ƃ������Ƃɂ��܂��傤�B�J���r���̂��̂��R�~�b�g����̂́A�udevelopment�v�Ƃ����u�����`�ɂ��܂��B�����āA��Ƃ� development ����g�s�b�N�u�����`��؂��čs���܂��B

��������ς���ƁA�Ȃɂ���Ƃ�����Ƃ��ɂ� development �u�����`���� topic �u�����`��؂��čs���܂��B�����āA���̍�Ƃ��I�������Adevelop �u�����`�ł��̃g�s�b�N�u�����`�� merge ���܂��B������J��Ԃ��āAdevelopment �u�����`�̏�Ԃ��u�����[�X�ł�����́v�ɂȂ�����Amaster �u�����`���� development �u�����`�� merge ���܂��B

����Ƃ����ЂƂA���łɃ����[�X���Ă��܂������̂ɕs������������Ƃ��ɂ�����ً}�ŏC�����Ȃ���΂Ȃ�Ȃ��Ƃ��ɂ́Amaster �u�����`���� hotfix �u�����`��؂��āA�����ŏC���������e�� master �u�����`�� merge ���邱�Ƃɂ��܂��傤�B����ŁA�J�����̂��̂��}���Ń����[�X�����ɁA�ً}�̑Ή������͐�Ƀ����[�X�łɑg�ݍ��݂��Ƃ��ł��܂��ˁB

�����āA���ً̋}�Ή��������Ƀ����[�X���ꂽ�Ȃ�Ahotfix ����荞�܂ꂽ master �u�����`�� development �Ƀ}�[�W���邱�Ƃɂ��܂��傤�B���̂悤�ɉ^�p���邱�ƂŁA�J���łɂ��A�����[�X�łł̏C���𔽉f���邱�Ƃ��ł��܂��B


### �݂�Ȃł���郊�|�W�g���̍쐬
    $ git clone --bare ������ ����������
�Ƃ��������� --bare ��t���ă��|�W�g���𕡐�����ƁA��ƃf�B���N�g���Ȃ��ŁA���|�W�g�������𕡐����邱�Ƃ��ł���̂ł��B

�u�݂�ȂŐG�郊�|�W�g���v�Œ��ڍ�Ƃ��s�����Ƃ͂Ȃ��̂ŁA���̃��|�W�g���ɂ͍�ƃf�B���N�g���͗v��Ȃ��ł���ˁB�Ȃ̂ŁA�݂�ȂŐG�郊�|�W�g�������Ƃ��ɂ� --bare �t���ŕ������܂��傤�B�݂�ȂŐG�郊�|�W�g�������������ubare repository�v�ō��̂ɂ́A���͂����ЂƂ��R������̂ł����A����͂܂����߂Đ������܂��傤�B���Ȃ݂ɁAbare���|�W�g���̖��O�́A�Ō�Ɂu.git�v��t����̂����K�ƂȂ��Ă܂��B

���āA����Ŗ����Ɂu�݂�ȂŐG�郊�|�W�g���v���o���オ��܂����B�����clone���Ďg���B�i�Ȃ�ŁH�H�j

### �����[�g���|�W�g���Ƃ�
�u���̃��|�W�g���ɃR�~�b�g���e�𔽉f���������v�Ƃ��u���̃��|�W�g���̕ύX���e���擾���Ă������v�Ƃ����悤�Ȃ��Ƃ����邽�߂ɂ́A�u���̃��|�W�g���v�ɂ����郊�|�W�g�����A�u�����[�g���|�W�g���v�Ƃ��ēo�^���Ă����Ȃ���΂Ȃ�܂���B

�t�̌�����������ƁA�茳�̃��|�W�g���̃R�~�b�g���e��ʂ̃��|�W�g���ɔ��f��������A�ʂ̃��|�W�g���̃R�~�b�g���e���茳�̃��|�W�g���ɔ��f�������ꍇ�ɂ́A�u�����[�g���|�W�g���v�Ƃ��āA���̃��|�W�g����o�^���Ă����K�v������A�Ƃ������Ƃł��B

���Ȃ݂ɁAgit clone �Ń��|�W�g�����茳�ɕ������Ă����ꍇ�AGit ���񂪏���� clone ���̃��|�W�g�����A�uorigin�v�Ƃ������O�̃����[�g���|�W�g���Ƃ��ēo�^���Ă����̂ł��B����ŁAclone���Ă������|�W�g������R�~�b�g���e���茳�Ɏ�荞�񂾂�A�茳�̃��|�W�g���̃R�~�b�g���e��clone���Ă������|�W�g���ɔ��f�ł��܂��ˁIGit ������Ă΋C�������I

    $ git remote
    origin

�͂��Aorigin ���\������܂����B����͂܂�A�u�����[�g���|�W�g���Ƃ��� origin �Ƃ������|�W�g�����o�^����Ă����v�Ƃ������Ƃł��B

    $ git log --graph --date-order --all --pretty=format:'%h %Cred%d %Cgreen%ad %Cblue%cn %Creset%s'  --date=short
    * 7730680  (HEAD -> master, origin/master, origin/development, origin/HEAD) 2017-01-05 TAKASHI add cat_lover_said.txt
origin/master, origin/development, origin/HEAD �Ƃ����݂��̃u�����`������܂��ˁB�����͂��ꂼ��A
- origin �����[�g���|�W�g��(�܂� clone ��)�� master �u�����`
- origin �����[�g���|�W�g���� development �u�����`
- origin �����[�g���|�W�g����HEAD

��\���Ă��܂��Bgit clone ������ƁA�N���[�����ɑ��݂���R�~�b�g�ƃu�����`���A�茳�ɕ������Ă��܂��B���̂Ƃ��A�u�����`�́u�����[�g�u�����`�v�Ƃ��ăR�s�[����Ă��܂��B�����[�g���|�W�g������R�s�[����Ă����u�����`�Ȃ̂ŁA�u�����[�g�u�����`�v�ł��B

���́A�茳�� master �u�����`�ƁAclone �����畡������Ă����O�́u�����[�g�u�����`�v�����݂��Ă����Ԃł��B

�����̃����[�g�u�����`�́A���Ƃ��Ɓu�����̕��v�ł͂���܂���B�u�݂�Ȃ̂��́v�ł��B�Ȃ̂ŁA���̃����[�g�u�����`��I�����č�Ƃ����邱�Ƃ͂ł��܂���B�ł́A�����[�g���|�W�g���ɓ��e�𔽉f���������悤�ȕύX���茳�ōs�����߂ɂ́A�ǂ�����΂����̂ł��傤���H

�菇�͈ȉ��̒ʂ�ł��B

1. �����[�g���|�W�g���́A���f�������u�����`���u�ǐՁv���邽�߂̃u�����`���茳�̃��|�W�g���ɍ쐬����
1. ���̃u�����`��ŕύX���s���A�R�~�b�g����
1. ���̃R�~�b�g���A�u�ǐՁv���Ă��郊���[�g�u�����`�ƃ����[�g���|�W�g���ɔ��f����

�uorigin/development�v��ǐՂ��� development �u�����`���A�茳�ɍ쐬���܂��傤�B�����[�g�u�����`��ǐՂ���u�����`���쐬���邽�߂ɂ́A 

    $ git branch ���茳�̃u�����`�̖��O�� ���ǐՂ����������[�g�u�����`�̖��O��

�ł��B����Ă݂܂��傤�B

    $ git branch development origin/development
    Branch development set up to track remote branch development from origin.
�udevelopment �u�����`�́A origin ���痈�� development �����[�g�u�����`��ǐՂ���悤�ɐݒ肳�ꂽ��v�ƌ����܂����ˁB���������ł��B

����Ŏ茳�� development �u�����`�ōs�������f�� origin �� development �u�����`�ɔ��f������A���̋t�� origin �� development �u�����`�ōs��ꂽ�ύX�������� development �u�����`�ɓK�p���邱�Ƃ��ł���悤�ɂȂ�܂����B

�Ƃ���ŁA�����ق� git clone ���Ă����Ƃ��ɁA���łɎ茳�� master �u�����`�����݂��Ă��܂����ˁH ����͂ǂ��������Ƃł��傤���B

git clone ���s�����Ƃ��A�܂��̓N���[�����̃��|�W�g���ɑ��݂���R�~�b�g�ƃu�����`���茳�ɕ��������̂͏�Ō����ʂ�ł��B���́AGit ����͂��̂��ƁAorigin/master �u�����`��ǐՂ��� master �u�����`������Ɏ茳�ɍ쐬���Ă���āA����ɍ�ƃf�B���N�g�����ɂ��� master �u�����`�� checkout ����Ƃ���܂Ŏ����ł���Ă���Ă����̂ł��B


### �����[�g���|�W�g���̎蓮�ǉ�
remote���|�W�g����ǉ����邽�߂ɂ́A

    $ git remote add <�����[�g���|�W�g���̖��O> <�����[�g���|�W�g���̏ꏊ>

�ł��B

�A���b�I�H origin/* �u�����`���Ȃ��ł��ˁI�H

���́u�����[�g���|�W�g���͂����ɂ����v�Ƃ����ݒ�͂��܂������A���̃����[�g���|�W�g���ɑ��݂��Ă���R�~�b�g��u�����`���茳�̃��|�W�g���ɃR�s�[���Ă���Ƃ���܂ł͂���Ă��܂���B

�ł́A�����[�g���|�W�g���ɑ��݂���R�~�b�g��u�����`���茳�Ɏ����Ă��܂��傤�B���̂��߂Ɏg���R�}���h���A git fetch �ł��B

    $ git fetch �������[�g���|�W�g���̖��O��

�ŁA�����[�g���|�W�g���̒��g���茳�Ɏ����ė���܂��B����Ă݂܂��傤�B

    $ git fetch origin
    From path/to/shared_repo
     * [new branch]      development -> origin/development
     * [new branch]      master     -> origin/master

�ӂ��̐V�����u�����`�����܂�Ă��܂��ˁB���̍������u�����[�g���|�W�g���ł̃u�����`�̖��O�v�A���̉E�����u�茳�ɃR�s�[���ꂽ�����[�g�u�����`�v�ł��B

���āA����ŏ����� OK �ł��傤���H

���́A�܂������͖��[�ł͂���܂���B�茳�ɂ� development �u�����`�� master �u�����`�����݂��Ă��܂����A���̃u�����`�����ꂼ�� origin/development �� origin/master ��ǐՂ���悤�ɂ��Ȃ��ƁA�茳�ōs�����ύX�� origin/development �� origin/master �ɔ��f����܂���ˁB�Ȃ̂ŁA���͎茳�� master, development �����ꂼ�� origin/master, origin/development ��ǐՂ���悤�ɐݒ肵�܂��傤�B

���̂��߂ɂ́A

    $ git branch --set-upstream-to=���ǐՂ����������[�g�u�����`�� ���茳�̃u�����`��

�Ƃ����R�}���h�𗘗p���܂��B


### �݂�Ȃł���郊�|�W�g���@�܂Ƃ�
- �茳�̃��|�W�g���ł̕ύX���e�𑼂̃��|�W�g���ɔ��f������A�t�ɑ��̃��|�W�g���ł̕ύX���e�������̃��|�W�g���ɔ��f���邽�߂ɂ́A���̃��|�W�g�����u�����[�g���|�W�g���v�Ƃ��ēo�^���Ă����Ȃ��Ă͂����Ȃ�
    - git clone �Ń��|�W�g���𕡐������ꍇ�AGit ������ɂ��̕������Ƃ��uorigin�v�Ƃ������O�Ń����[�g���|�W�g���ɓo�^���Ă����
    - �����łȂ��ꍇ�́A git remote add <���O> <�ꏊ> �Ń����[�g���|�W�g����o�^�ł���
- �����[�g���|�W�g���ɑ��݂���u�����`��R�~�b�g���茳�ɕ������邽�߂ɂ́A git fetch �������[�g�u�����`�̖��O�� ���g��
    - git clone �Ń��|�W�g���𕡐������ꍇ�́Aclone �̒i�K�ł��łɎ茳�̃��|�W�g���ɕ�������Ă���B
    - �����[�g���|�W�g���ɑ��݂���u�����`�́A�茳�̃u�����`�ɃR�s�[���Ă���Ƃ��ɂ́u�����[�g�u�����`�v�Ƃ����`�ŃR�s�[�����B
- �����[�g�u�����`�ɒ��ڃR�~�b�g���邱�Ƃ͂ł��Ȃ��̂ŁA���̃����[�g�u�����`��ǐՂ��邽�߂̃u�����`���茳�̃��|�W�g���ɍ쐬����K�v������B
    - ���郊���[�g�u�����`��ǐՂ���V�����u�����`���쐬�������ꍇ�́Agit branch <�V�����u�����`��> <�����[�g�u�����`��>
    - ���łɎ茳�ɑ��݂���u�����`�ł��郊���[�g�u�����`��ǐՂ������ꍇ�� git branch --set-upstream-to=���ǐՂ����������[�g�u�����`�� ���茳�̃u�����`��


### �݂�Ȃł����@push pull
    $ git checkout -b feature/unify_styles development

����́ufeature/unify_styles�v�Ƃ������O�̃u�����`��؂��Ă��܂��ˁB����́A�u���̃u�����`�̓t�B�[�`���[�u�����`����v�Ƃ������Ƃ��킩��₷�����邽�߂ɁA�����������O��t���������ł��B�������A���̂��Ƃ� development �Ƃ����w�������ɂ��Ă���܂��B

����͂ǂ��������Ƃ��ƌ����ƁA�V�����u�����`���u�ǂ�����v�؂�̂����w�肵���̂ł��B

�����炭�A���܂䂤�����ł��邠�Ȃ��� master �u�����`��I�����Ă����ł��傤�B���̏�Ԃ�git branch -b ���V�������u�����`�̖��O���Ƃ���ƁAmaster �u�����`���番�򂷂�u�����`���؂��܂��B�������A

    $ git branch -b ���V�������u�����`�̖��O�� �����򌳁�

�Ƃ��邱�ƂŁA�����I�Ɂu�ǂ�����u�����`�𕪊򂳂���̂��v���w�肷�邱�Ƃ��ł���̂ł��B


### �����[�g���|�W�g�������݂��Ȃ� -> push
���āA�茳�̃��|�W�g���̕ύX�������[�g���|�W�g���ɔ��f�����邽�߂ɂ͂ǂ�����̂ł��������H �����ł��A�ǐՃu�����`�ł��ˁB����Ȃ�΁Aorigin/hotfix ��ǐՂ���u�����`�����΁c�c�c�c�A�Ƃ����܂ōl���āA�u�A�����v�ƂȂ�܂����B�������� origin/hotfix �Ƃ��������[�g�u�����`�����݂��Ȃ��c�c�B

    $ git push �������[�g���|�W�g���̖��O�� ���茳�̃u�����`��:�������[�g�ɍ�肽���u�����`��

����Łu�����[�g���|�W�g���ɐV�����u�����`�𕡐��v�ł���

    $ git push origin hotfix:hotfix
    Counting objects: 5, done.
    Delta compression using up to 8 threads.
    Compressing objects: 100% (2/2), done.
    Writing objects: 100% (3/3), 371 bytes, done.
    Total 3 (delta 1), reused 0 (delta 0)
    To ../shared_repo.git
     * [new branch]      hotfix -> hotfix
 
 �d�v�Ȃ͍̂Ō�� 2 �s�ł��B�ushred_repo.git �ɑ΂���: �E�V�����u�����` hotfix -> hotfix�v�Ƃ��������ł��ˁB����B�݂�ȂŐG�郊�|�W�g����hotfix���쐬���邱�Ƃ��ł��܂����B
 
 ���Ȃ݂ɁA����̂悤�ɁA�茳�̃��|�W�g���ł̃u�����`�̖��O�ƃ����[�g���|�W�g���̃u�����`�̖��O������̏ꍇ�́A

    $ git push <�����[�g���|�W�g���̖��O�� ���u�����`�̖��O��

�ł� OK �ł��B


���āA����Łu�݂�ȂŐG�郊�|�W�g���v��hotfix�u�����`���쐬���邱�Ƃ��ł��܂����B���Ⴀ�A�茳�� hotfix �u�����`�����̃����[�g�u�����`��ǐՂ���悤�ɐݒ肵�Ă����܂��傤�B

    $ git branch --set-upstream-to=origin/hotfix hotfix

�͂��A�����ł��ˁB


### ���L���|�W�g���Ƀ}�[�W����

���L���|�W�g���𒼐ڂ����邱�Ƃ͂ł��܂���B���������Ƃ��ɂ͂ǂ�����̂ł������H �����ł��A�u�ǐՃu�����`�v��ύX����΂����̂ł����ˁB���A���L���|�W�g���� master �u�����`��ǐՂ��Ă���̂́A�茳�� master �u�����`�ł��B

�ł́Ahotfix �̓��e���茳�� master �u�����`�� merge ���܂��傤�B����͊ȒP�ł��ˁB

    $ git checkout master
    $ git merge --no-ff hotfix 

�ł��B�ł͌��݂̃O���t���m�F���܂��傤�B

    $ git log --graph --date-order --all --pretty=format:'%h %d %ad %cn %s' --date=short
    *   0672d53  (HEAD -> master) 2017-01-05 TAKASHI Merge branch 'hotfix'
    |\
    | * 315f673  (origin/hotfix, hotfix) 2017-01-05 TAKASHI �����������Ƃ����\���͂܂����̂ŏC��
    |/
    * 7730680  (origin/master, origin/development, development) 2017-01-05 TAKASHI add cat_lover_said.txt

�茳�� master �u�����`�́A�ł����Ẵ}�[�W�R�~�b�g���w���Ă��܂��B�������Aorigin/master �͂܂����̃}�[�W�R�~�b�g���w���Ă��܂���ˁB��������̂͂��A���������܂����̃R�~�b�g�͕ύX�҂̎茳�̃��|�W�g���ɂ������݂��܂���B

������ git status ���m�F�����

    $ git status
    On branch master
    Your branch is ahead of 'origin/master' by 2 commits.
      (use "git push" to publish your local commits)
    nothing to commit, working directory clean

���A���߂Č���\�����o�Ă��܂����B�ȂɂȂɁH

�u�N�̃u�����`�� origin/master ���� 2 �R�~�b�g�i��ł��邺�I(�����N�̎茳�̃R�~�b�g�����J���Ă��܂�������΁A git push ����Ƃ������I)�v�������ł��B

�ł́AGit����Ɍ���ꂽ�Ƃ���A������ git push �ŋ��L���|�W�g���ɂ��̕ύX�����J���܂��傤�I


    $ git push
    warning: push.default is unset; its implicit value has changed in
    Git 2.0 from 'matching' to 'simple'. To squelch this message
    and maintain the traditional behavior, use:

      git config --global push.default matching

    To squelch this message and adopt the new behavior now, use:

      git config --global push.default simple

    When push.default is set to 'matching', git will push local branches
    to the remote branches that already exist with the same name.

    Since Git 2.0, Git defaults to the more conservative 'simple'
    behavior, which only pushes the current branch to the corresponding
    remote branch that 'git pull' uses to update the current branch.

    See 'git help config' and search for 'push.default' for further information.
    (the 'simple' mode was introduced in Git 1.7.11. Use the similar mode
    'current' instead of 'simple' if you sometimes use older versions of Git)

    Counting objects: 1, done.
    Writing objects: 100% (1/1), 227 bytes | 0 bytes/s, done.
    Total 1 (delta 0), reused 0 (delta 0)
    To ../shared_repo.git
       7730680..0672d53  master -> master

�ł́Awarning �̓��e��ǂ�ł݂܂��傤�B

    �x���F push.default ���ݒ肳��ĂȂ���Bpush.default���ݒ肳��Ă��Ȃ��Ƃ�
    �̒l�́AGit 2.0 �Łumatching ���� simple�v�ɕύX������B
    �ȉ��̂悤�ȃR�}���h��łƁA���ケ�̃��b�Z�[�W�͏o�Ȃ��Ȃ邵�A
    �ύX����Ă�������܂łƓ��������������

      git config --global push.default matching

    �ȉ��̂悤�ȃR�}���h��łƁA���ケ�̃��b�Z�[�W�͏o�Ȃ��Ȃ邵
    2.0�ȍ~�̐V��������������悤�ɂȂ��B

      git config --global push.default simple

    �����Əڂ�������������������΁A'git help config' �Ƒł��āA
    'push .default'�̕�����T���Ă����ȁB
    (���Ȃ݂�'simple'���[�h�� Git 1.7.11 ����g����񂾁B�����Â� Git ��
    ���@�[�W�������g���悤�Ȃ�A�����悤�� 'current' ���ă��[�h���g���Ă���)

�������ł�


���� push.default �Ƃ����̂́Agit push �������ɕt������ push �����s�����Ƃ��ɁAGit ���񂪂ǂ̂悤�ȓ���������̂���ݒ肷��ݒ荀�ڂł��B'matching' ���[�h���ƁA���I������Ă���u�����`���ǂ̃u�����`���ɂ͊֌W�Ȃ��A�u�茳�ɂ��邷�ׂĂ̒ǐՃu�����`�̕ύX�������[�g�ɔ��f����v�Ƃ��������ɂȂ�܂��B'simple'���[�h�́A�u���I������Ă���u�����`���ǐՃu�����`�ł���΁A�茳�̃u�����`�̕ύX���e�������[�g�ɔ��f����v�Ƃ��������ɂȂ�܂��B

����͏�L�ݒ�́A�����Ȃ킸�A���L�ɂ�push�����B

    $ git push [�����[�g���|�W�g��] [���[�J���̃u�����`��]:[�����[�g�̃u�����`��]
    $ git push origin master:master


### ���Ǝn��
�����Ƀ����[�X���ꂽ�����ł��B�ł́A���Ǝn�������܂��傤�B��������Ȃ���΂Ȃ�Ȃ��̂͑�܂��Ɉȉ��̓�ł��B

- hotfix �u�����`�͂����p�����Ȃ̂ŁA�茳����������[�g����������Ă��܂�
- �ً}�����[�X�ɂ��ύX���e���A�J���u�����`�ɂ����f������

�����A�ł͂���Ă����܂��傤�B�茳�� hotfix �u�����`�������̂͊ȒP�ł���

    $ git branch -d hotfix

���������Ă������e�𔽉f���邽�߂ɒǐՃu�����`���K�v�Ȃ񂾂��Ǐ��������Ă������e�𐶂ނ��߂ɂ͏����K�v�������� push �ł��Ȃ��c�c�B�Ƃ��������ł��ˁB����Ȃ킯�Ȃ�ŁA�����[�g�̃u�����`���������߂ɂ͂��̂��߂̃R�}���h��ʂɑłK�v������܂��B

    $ git push origin :hotfix

�ł́A���́A hotfix �őΉ����ꂽ���e�����f����Ă��� master ���A development �Ɏ�荞�݂܂��傤�B

    $ git checkout development
    $ git merge --no-ff master

����������[�g�ɔ��f

    $ git push


### �ʂ̊J���ҁFmerge
���āA����������������ă����[�g���|�W�g���̓��e���擾���Ă��āA�蓮�� merge ����̂͐������邢�ł��ˁB���邷���ł��B���̂��߂ɗp�ӂ���Ă���� git pull �ł��B

git pull �́A�ufetch ���ă}�[�W�v�Ƃ�����A�̓���������ł���Ă���܂��B���i�͂�������g���Ɨǂ��ł��傤�B�������A�C�����Ă��������B�����ق� "git pull �́ufetch ���ă}�[�W�v���Ƃ�����A�̓���������ł���Ă����" �Ƃ����܂����B�����ł��A�u�}�[�W�v���s���̂ł��B���̂��߁Agit pull ���s���Ɓu�R���t���N�g�v���N����\��������܂��B�ł��A�������Ȃ��̓R���t���N�g���������������ɂǂ�����΂������A�m���Ă��܂��ˁB�Ȃ�|����Ȃ��Ă����v�B���������ċ����𒼂��蓮�Ń}�[�W�R�~�b�g�����΂����̂ł��B

���R�A���̃}�[�W�R�~�b�g�́u�茳�v�ɂ����Ȃ��}�[�W�R�~�b�g�Ȃ̂ŁA�K�؂ɋ��L���|�W�g���� push ����K�v���o�Ă���ł��傤�B�ł��A�������Ȃ��̓����[�g���|�W�g���Ǝ茳�̃��|�W�g���̊֌W��K�؂Ƀn���h�����邱�Ƃ��ł���悤�ɂȂ��Ă��܂��B������Ȃɂ��|���Ȃ��ł��ˁB


### git push ������Ђ낢

���āA����͉������Ȃ��X���[�X�ɂ��Ƃ��^�т܂������Agit push ���������邽�߂ɂ́A����������܂��B

- �����[�g���|�W�g�����Abare ���|�W�g���ł���
    - �o���Ă܂����H bare ���|�W�g���B��ƃf�B���N�g���𔺂�Ȃ����|�W�g���ł����ˁB��������Ƃ��Ă�Ƃ���ɂǂ������� push ����Ă����獬�������Ⴂ�܂���ˁB���̂��߁A��ƃf�B���N�g���������Ȃ� bare ���|�W�g���ւ���Ȃ��ƁApush �͎󂯓���Ă��炦�܂���B
- �����[�g���|�W�g���ւ̏������݌����������Ă���
    - ����͓����t�@�C���V�X�e����̏������݌��̂��郊�|�W�g������������ push �\����������ǁA���Ƃ��� Github �̑��l�̃��|�W�g�����Ƃ��A���������u�������݌��v�̂Ȃ����|�W�g���ɑ΂��� push ���Ă��������݂͂ł��܂���B�܂��A���R�ł��ˁB
- �茳�̃����[�g�u�����`�������[�g���|�W�g���Ɂu�ǂ����āv����
    - �����̎茳�ɂ���R�~�b�g���������[�g�̃R�~�b�g�̂ق����u��Ɂv�i��ł�����A���̃R�~�b�g�́u����B�e�R�~�b�g���Ⴄ�c�c�v����ǂ�����΂����񂾂낤�c�c�ƂȂ��Ă��܂��܂��B���̂悤�ȏꍇ�ɂ́A�K�X git fetch ����� merge �� git pull ���s����(���̍ۂ� merge �ł̓R���t���N�g����������\��������܂�)�A�茳�̃����[�g�u�����`�������[�g���|�W�g���ɒǂ������Ă��� push ���Ă��������B
- ���łɃ����[�g���|�W�g���� push �ς݂̃R�~�b�g���A�茳�̃��|�W�g���ŉ��ς���Ă��Ȃ�
    - push �ς݂̃R�~�b�g�� git rebase �� git commit --amend �ŉ��ς���Ă��܂��ƁA�����[�g���|�W�g���Ǝ茳�̃��|�W�g���̊Ԃŕs�������N�����Ă��܂��܂��B

### push, pull �܂Ƃ�
- �����[�g���|�W�g���Ɏ茳�̕ύX�𔽉f�������Ȃ�Agit push
    - �ǐՃu�����`�ɑ΂��Ă̕ύX�͂��̂܂� git push
    - �V�����u�����`����肽���Ȃ� git push �������[�g���|�W�g���̖��O�� ���茳�̃u�����`��:�������[�g�̃u�����`�̖��O��
    - �u�����`���폜�������Ȃ� git push �������[�g���|�W�g���̖��O�� :�������[�g�̃u�����`�̖��O��
- �����[�g���|�W�g������茳�ɕύX�������Ă������Ȃ� git fetch
    - �����[�g���|�W�g���̃R�~�b�g�ƃu�����`�������Ă���
    - �����[�g���|�W�g���̃u�����`�̓����[�g�u�����`�Ƃ��č����
- fetch �̂��ł� merge ���ꏏ�ɂ�肽���Ȃ�Agit pull

����Q�l�ɂȂ�^�p���@�@�@
1. http://keijinsonyaban.blogspot.jp/2010/10/a-successful-git-branching-model.html�@�@
2. https://gist.github.com/Gab-km/3705015�@�@
